#!groovy​

podTemplate(label: 'test', containers: [
    containerTemplate(name: 'node', image: 'node:8', ttyEnabled: true, command: 'cat'),
    containerTemplate(name: 'pm2', image: 'keymetrics/pm2:8-alpine', ttyEnabled: true, command: 'cat')
  ]
) {
  node('test') {
    environment {
        CI = 'true'
    }
    container('node') {
      stage('Build') {
          sh 'npm install'
          sh 'npm install pm2 -g'
      }
    }

    container('pm2') {
      stage('Deploy') {
          sh 'pm2 start index.js'
      }
    }
  
  }
}
    