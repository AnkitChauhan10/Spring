pipeline {
    agent any
    stages {
        stage('Pull Docker Image') {
            steps {
                script {
                    def dockerImage = docker.image('spring/spring:lts')
                    withCredentials([usernamePassword(credentialsId: '4e41affb-db9b-4dae-b6c7-8182465b8d89', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                        dockerImage.withRegistry('https://index.docker.io/v1/', DOCKERHUB_USERNAME, DOCKERHUB_PASSWORD)
                        dockerImage.pull()
                    }
                }
            }
        }
        // Other stages in your pipeline...
    }
}
