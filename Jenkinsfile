pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/EDRV02/lbg-vat-calculator.git'
            }
        }
        stage('Install') {
            steps {
                sh "npm install"
            }
        }
        stage('Test') {
            steps {
                sh"npm test"
            }
        }
    
    stage('SonarQube Analysis') {
        environment {
            scannerHome = tool 'sonarqube'
        }
        steps {
            withSonarQubeEnv('sonar-qube-1') {
                sh "${scannerHome}/bin/sonar-scanner"
            }
            timeout(time: 10, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
}