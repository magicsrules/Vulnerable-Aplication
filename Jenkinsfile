pipeline {
  agent any
  stages {
    stage('SonarQube analysis') {
      steps {
        script {
          def scannerHome = tool 'SonarQubeScanner';
          withSonarQubeEnv('SonarQubeServer') {
            sh "${tool("SonarQubeScanner")}/bin/sonar-scanner -Dsonar.projectKey=dvwa -Dsonar.projectName=DVWA"
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
    sonarqube = 'SonarQubeServer'
  }
}









