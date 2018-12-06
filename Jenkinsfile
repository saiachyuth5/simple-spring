pipeline {
  environment {
    registry = “achyuth007/simple-spring”
    registryCredential = ‘dockerhub’
  }
  agent any
  stages {
    stage(‘Cloning Git’) {
      steps {
        git ‘https://github.com/saiachyuth5/simple-spring.git'
      }
    }
    stage(‘Building image’) {
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
