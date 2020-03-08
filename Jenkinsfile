pipeline {
 
 agent any
 
 environment {
    PROJECT_ID = "devops-aditya"
    CLUSTER_NAME = 'k8-demo'
    LOCATION = 'us-central1-c'
    CREDENTIALS_ID = 'devops-aditya'
  }
   
    stages {
     stage('Checkout SCM') {
      steps {
       checkout scm
      }
     }
    stage('Build package') {

        steps {
        echo "Cleaning and packing.."
         sh 'mvn clean package'
        }
    }
     stage('Test') {
      steps {
       echo "Testing.."
       sh 'mvn test'
      }
     }
     stage('Build and push Docker Image') {
      steps{
        script {
         appimage = docker.build( "gcr.io/devops-aditya:${env.BUILD_ID}")
         //docker.withRegistry('https://registry.hub.docker.com','docker-hub-credentials') {
           docker.withRegistry('https://gcr.io','gcr:gcr_creds') {
            appimage.push("${env.BUILD_ID}")
          }
        }
      }
    }
     stage('Deploy to Kubernetes') {
      steps {
       echo "Deploying to Kubernetes Cluster.."
       sh 'ls -ltr'
       sh 'pwd'
       sh "sed -i 's/tagversion/${env.BUILD_ID}/g' deployment.yaml"
       step([$class: 'KubernetesEngineBuilder', projectId: env.PROJECT_ID, clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: 'deployment.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
       echo "Deployment to Kubernetes cluster completed.."
      }
     }
    }
}
