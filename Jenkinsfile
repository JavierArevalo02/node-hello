pipeline {
  agent any

  tools {
    nodejs "Endava"
  }
  parameters {
    string(name: 'container_name', defaultValue: 'HomeworkEndava', description: 'Nombre del contenedor de docker.')
    string(name: 'image_name', defaultValue: 'nodeEndava', description: 'Nombre de la imagene docker.')
    string(name: 'tag_image', defaultValue: 'endava', description: 'Tag de la imagen de la página.')
    string(name: 'container_port', defaultValue: '3000', description: 'Puerto que usa el contenedor')
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

    stage('build') {
      steps {
        dir('node-hello') {
          script {
             try {
              sh 'docker stop ${container_name}'
              sh 'docker rm ${container_name}'
              sh 'docker rmi ${image_name}:${tag_image}'
            } catch (Exception e) {
              echo 'Exception occurred: ' + e.toString()
            }
            sh 'docker build -t ${image_name}:${tag_image} .'
          }
        }
      }
    }

    stage('deploy'){
      steps{
        sh 'docker run -d -p ${container_port}:3000 --name ${container_name} ${image_name}:${tag_image}'
      }
    }
  }
}