#!groovy​

podTemplate(label: 'test', containers: [
  containerTemplate(name: 'node', image: 'node:8', ttyEnabled: true, command: 'cat'),
  containerTemplate(name: 'pm2', image: 'keymetrics/pm2:8-alpine', ttyEnabled: true, command: 'cat')
  ])
]) {
  node('test') {
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
}
    