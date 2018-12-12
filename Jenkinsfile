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
          docker.withRegistry( "https://registry.hub.docker.com", registryCredential ) {
           // dockerImage.push()
          app.push("${env.BUILD_NUMBER}")
          }
        }
      }
    }
    stage('Deploy to ACS'){
      steps{
          acsDeploy(azureCredentialsId: 'dbb6d63b-41ab-4e71-b9ed-32b3be06eeb8',
            resourceGroupName: 'ilink',
            containerService: 'gajacluster | AKS',
            configFilePaths: '**/sample.yaml',
            enableConfigSubstitution: true
                    )
      }
    }
  }
}
