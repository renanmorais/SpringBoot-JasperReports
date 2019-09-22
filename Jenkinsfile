pipeline {
    agent any
    options {
        timestamps()
    }
    environment {
        pipeline = "${env.JOB_NAME}"
    }

    stages {
      stage('SonarQube Analysis') {
        environment {
            scannerHome = tool 'SonarQube Scanner'
        }
        steps {
            withSonarQubeEnv('sonarqube') {
                sh "${scannerHome}/bin/sonar-scanner -Dsonar.sources=. -Dsonar.projectKey=renanmorais_sig -Dsonar.organization=renanmorais -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=59c64e0f99ed8246336c8837423c7968d6f2fc79"
            }
            timeout(time: 10, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
            }
        }
      }
    }
}
