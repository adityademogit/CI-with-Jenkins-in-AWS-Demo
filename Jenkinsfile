pipeline {
    
def app

    stages {
        stage('Build image') {
        parallel(

        app = docker.build("aditya4uhere/tomcat01")
        
        )
    }

    stage('Push image') {

        parallel (

        docker.withRegistry('https://hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("docker1")
        }
      )
    }
 }
}
