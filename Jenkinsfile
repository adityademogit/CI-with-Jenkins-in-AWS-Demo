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
    post {
        always {
            archiveArtifacts artifacts: 'project/target/*.war', fingerprint: true
}
