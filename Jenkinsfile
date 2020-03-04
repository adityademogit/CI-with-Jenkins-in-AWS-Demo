pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building .war artifact'
                sh 'mvn package'
            }
        }
    }
}
