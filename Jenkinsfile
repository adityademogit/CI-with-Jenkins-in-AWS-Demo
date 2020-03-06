pipeline {

 agent {
        docker {
            image 'aditya4uhere/tomcat01:latest'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    
    stages {
        
    stage('Build and Push image') {

        steps {
    checkout scm

    docker.withRegistry('https://hub.docker.com/repository/docker/aditya4uhere/tomcat01', 'docker-hub-credentials') {

        def customImage = docker.build("aditya4uhere/tomcat01:latest")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
    }
 }
}
