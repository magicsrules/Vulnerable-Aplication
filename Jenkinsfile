pipeline {
    agent any
    environment {
        projectName = "dvwa"
    }
stages {
    stage('SonarQube analysis') {
      steps {
        script {
          def scannerHome = tool 'sonarqube-scanner';
          withSonarQubeEnv('sonarqube') {
            sh "${tool("sonarqube-scanner")}/bin/sonar-scanner -Dsonar.projectKey=dvwa -Dsonar.projectName=DVWA"
          }
        }
      }
    }
  }
}
