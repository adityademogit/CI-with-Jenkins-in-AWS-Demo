pipeline {

    agent any
    
    stages {
        stage('Build image') {
            steps {

        app = docker.build("aditya4uhere/tomcat01")
            }
    }

    stage('Push image') {

        steps {

        docker.withRegistry('https://hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("docker1")
         }
        }
    }
 }
}
