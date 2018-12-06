pipeline {
  environment {
    registry = “achyuth007/simple-spring”
    registryCredential = ‘dockerhub’
  }
  agent any
  stages {
    stage(‘Build’) {
      steps{
        script {
          docker.build registry + “:$BUILD_NUMBER”
        }
      }
    }
     stage(‘Deploy’) {
      steps{
        script {
          docker.withRegistry( ‘’, registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
