pipeline {
    agent any
    environment {
        projectName = "SonarTest-Scanner"
    }
stages {
    stage ("SonarQube Scan") {
       steps {
          withEnv(["PATH="/home/covertech/jenkins_home/workspace/sonarqube-scanner]) {
             withSonarQubeEnv(installationName: 'covertech_sonarqube_1', credentialsId: 'sonarqubeSecret') {
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
