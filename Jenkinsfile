pipeline {
  agent any

  tools {
    nodejs "Endava"
  }

  parameters {
    string(name: 'install', defaultValue: 'npm install', description: 'Installar dependencias')
    string(name: 'start', defaultValue: 'npm start', description: 'Ejecutar index.js')
  }

  stages {
    stage('prepare') {
      steps {
        git branch: 'master', url: 'https://github.com/JavierArevalo02/node-hello.git'
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