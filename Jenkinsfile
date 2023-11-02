pipeline {
    agent any
    stages {
        stage('Pull Docker Image') {
            steps {
                script {
                    def dockerImage = docker.image('ankitchauhan18/spring/spring:lts')
                    dockerImage.pull()
                }
            }
        }
    }
}
