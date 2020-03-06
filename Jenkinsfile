pipeline {
 
 environment {
    registry = "aditya4uhere/devops:1.0.1"
    registryCredential = 'docker-hub-credentials'
    dockerImage = ''
  }

 agent any
    
    stages {
        
    stage('Build image') {

        steps {
    checkout scm
    script {
          dockerImage = docker.build registry
        }
    }
}
     stage ('Push Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
 }
}
