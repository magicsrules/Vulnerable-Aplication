node('master') {
    def projectName = 'SonarScanner'
stage("Sonar Scan") {
          withEnv(["PATH=/opt/sonarqube/bin/sonar-scanner"]) {
            withSonarQubeEnv(installationName: 'covertech_sonarqube_1', credentialsId: '2436567453f1') {
            sh "sonar-scanner \
                -Dsonar.projectKey=${projectName} \
                -Dsonar.sources=. \
                -Dsonar.host.url=${env.SONAR_HOST_URL} \
                -Dsonar.login=${env.SONAR_AUTH_TOKEN} \
                -Dsonar.projectName=${projectName} \
                -Dsonar.projectVersion=${env.BUILD_ID}"
         }
      }
    }
  }
pipeline {
    agent any
    environment {
        projectName = "SonarScanner"
    }
stages {
    stage ("SonarQube Scan") {
       steps {
          withEnv(["PATH=/opt/sonarqube/bin/sonar-scanner"]) {
             withSonarQubeEnv(installationName: 'covertech_sonarqube_1', credentialsId: '2436567453f1') {
               sh "sonar-scanner \
                 -Dsonar.projectKey=${projectName} \
                 -Dsonar.sources=. \
                 -Dsonar.host.url=${env.SONAR_HOST_URL} \
                 -Dsonar.login=${env.SONAR_AUTH_TOKEN} \
                 -Dsonar.projectName=${projectName} \
                 -Dsonar.projectVersion=${env.BUILD_ID}"
           }
         }
       }
     }
  }
}
