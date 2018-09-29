pipeline {
    agent {
        docker {
            image 'node:8'
            image 'keymetrics/pm2:8-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm install pm2 -g'
            }
        }
        stage('Deploy') {
            steps {
                sh 'pm2 start index.js'
            }
        }
    }
}
