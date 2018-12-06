pipeline {
  environment {
    registry = “achyuth007/simple-spring”
    registryCredential = ‘dockerhub’
  }
  agent any
  stages {
    stage(‘Building Image’) {
      steps{
        script {
          docker.build registry + “:$BUILD_NUMBER”
        }
      }
    }
     stage(‘Deploy Image’) {
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
