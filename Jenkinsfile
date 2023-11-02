pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    docker.build('spring:lts')
                }
            }
        }
        stage('Docker Push') {
            steps {
                script {
                    docker.withRegistry('https://hub.docker.com', 'docker-hub-credentials') {
                        docker.image('Spring:lts').push()
                    }
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deploy.yaml'
                sh 'kubectl apply -f serviceapp.yaml'
            }
        }
    }
}
