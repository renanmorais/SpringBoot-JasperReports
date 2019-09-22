pipeline {
  agent any
  stages {
    stage('SonarQube Analysis') {
      environment {
        scannerHome = 'SonarQube Scanner'
      }
      steps {
        withSonarQubeEnv('sonarqube') {
          sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=renanmorais_SpringBoot-JasperReports -Dsonar.organization=renanmorais -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=6b514a844f0e03071ce3e7585ee1f5a8760c77c5"
        }

        timeout(time: 10, unit: 'MINUTES') {
          waitForQualityGate true
        }

      }
    }
  }
  environment {
    pipeline = "${env.JOB_NAME}"
  }
  options {
    timestamps()
  }
}
