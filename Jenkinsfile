pipeline {
  agent any

  tools {
    nodejs "Endava"
  }

  stages {
    stage('prepare') {
      steps {
        git branch: 'master', url: 'https://github.com/JavierArevalo02/node-hello.git'
        dir('node-hello') {
          sh 'npm install'
        }
      }
    }

    stage('deploy') {
      steps {
        dir('node-hello') {
          sh 'npm start'
        }
      }
    }
  }
}