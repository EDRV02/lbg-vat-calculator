pipeline {
    agent any
    //hello

    stages {
        stage('checkout') {
            git branch: 'main', url: 'https://github.com/EDRV02/lbg-vat-calculator.git'
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
        }
    }
}