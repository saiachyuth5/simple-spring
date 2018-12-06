pipeline {
  environment {
    registryCredential = "dockerhub"
  }
  agent any
  stages {
    stage(‘Build’) {
      steps{
        script {
          app = docker.build("achyuth007/simple-spring")
        }
      }
    }
     stage(‘Deploy’) {
      steps{
        script {
          docker.withRegistry( ‘https://registry.hub.docker.com’, registryCredential ) {
           // dockerImage.push()
          app.push("${env.BUILD_NUMBER}")
          }
        }
      }
    }
  }
}
