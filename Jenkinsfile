pipeline {
    agent any
    stages {
        stage('Pull Docker Image') {
            steps {
                script {
                    def dockerImage = docker.image('spring/spring:lts')
                    dockerImage.pull()
                }
            }
        }
    }
}
