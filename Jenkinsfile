pipeline {
  agent any

  tools {
    nodejs "Endava"
  }

  parameters {
    string(name: 'install', defaultValue: 'npm install', description: 'Installar dependencias')
    string(name: 'start', defaultValue: 'npm start', description: 'Ejecutar index.js')
    string(name: 'stop', defaultValue: 'npm stop', description: 'parar ejecucion index.js')
  }

  stages {
    stage('stop') {
      steps {
        git branch: 'master', url: 'https://github.com/JavierArevalo02/node-hello.git'
        dir('node-hello') {
          sh '${stop}'
        }
      }
    }

    stage('prepare') {
      steps {
        dir('node-hello') {
          sh '${install}'
        }
      }
    }

    stage('deploy') {
      steps {
        dir('node-hello') {
          sh '${start}'
        }
      }
    }
  }
}