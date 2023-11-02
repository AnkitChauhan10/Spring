pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
               script {
                    def mavenHome = tool name: 'Maven', type: 'hudson.tasks.Maven$MavenInstallation'
                    def mavenExec = "${mavenHome}/bin/mvn"
                    sh "${mavenExec} clean package"
                }
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    docker.build('ankitchauhan18/spring/spring:lts')
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
