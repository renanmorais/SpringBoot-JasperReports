pipeline {
  agent any
  stages {
    stage('SonarQube Analysis') {
      steps {
        sh '''sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=renanmorais_calcprev-api -Dsonar.organization=renanmorais -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=b235baecf766a5522c23877f1d1ab93f12732bf9"
       '''
      }
    }
  }
  environment {
    scannerHome = 'SonarQube Scanner'
  }
}