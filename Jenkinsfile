pipeline {
  environment {
    dockerimagename = "bravinwasike/react-app"
    dockerImage = ""
  }
  agent any
  stages {
    stage('Checkout Source') {
      steps {
       git branch: 'main', url: 'https://github.com/khaleelmo/kubernetes.git'
      }
    }
    /*
    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }
    stage('Pushing Image') {
      environment {
               registryCredential = 'dockerhub-credentials'
           }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push("latest")
          }
        }
      }
    } */
    stage('Deploying  container to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yaml", "service.yaml")
          
          //bat ("kubectl apply -f .")
        }
      }
    }
  }
}
