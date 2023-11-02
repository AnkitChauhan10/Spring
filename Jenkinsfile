pipeline {
    agent any
    stages {
        stage('Pull Docker Image') {
            steps {
                script {
                    def dockerImage = docker.image('spring/spring:lts')
                    withCredentials([usernamePassword(credentialsId: 'af91c1f1-681d-413b-aa3f-1e73f6830004', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                        dockerImage.withRegistry('https://index.docker.io/v1/', DOCKERHUB_USERNAME, DOCKERHUB_PASSWORD)
                        dockerImage.pull()
                    }
                }
            }
        }
        // Other stages in your pipeline...
    }
}
