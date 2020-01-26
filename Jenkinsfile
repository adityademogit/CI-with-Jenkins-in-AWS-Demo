pipeline {
    agent any

    stages {
        stage('CI') {
            steps {
                echo 'Building artifact and pushing to Nexus..'
            }
        }
        stage('CD') {
            steps {
                echo 'Picking Artifact from CI and deploying in Tomcat..'
            }
        }
    }
}
