pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                checkout scm
            }
        }
        stage('Build image') {
            steps {
                script {
                    app = docker.build("bojanajancheska/kiii-homework-04")
                }
            }
        }
        stage('Push image') {
            steps {
                script {
                    // right parameter is jenkins credentials
                   docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
                        app.push("${env.BRANCH_NAME}-latest")
                   }
                }
            }
        }
    }
}
