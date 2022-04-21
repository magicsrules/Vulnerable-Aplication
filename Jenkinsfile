pipeline {
  agent any
  stages {
    stage('SonarQube analysis') {
      steps {
        script {
          def scannerHome = tool 'sonarqubeserver';
          withSonarQubeEnv('sonarqubeserver') {
            sh "${tool("sonarqubescanner")}/bin/sonar-scanner -Dsonar.projectKey=dvwa -Dsonar.projectName=DVWA"
          }
        }
      }
    }
    stage('Quality Gate') {
      steps {
        waitForQualityGate true
      }
    }
  }
  environment {
    sonarqube = 'sonarqubeserver'
  }
}









