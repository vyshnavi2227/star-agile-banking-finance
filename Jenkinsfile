pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/vyshnavi2227/star-agile-banking-finance.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Docker Login') {
            steps {
                withCredentials([string(credentialsId: 'doc_cred', variable: 'DOCKER_USERNAME')]) {
                    sh 'echo $DOCKER_HUB_PASSWORD | docker login -u vyshnavi2227doc --password-stdin'
                }
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t vyshnavi2227doc/banking-project:v1 .'
            }
        }
        stage('Docker Push') {
            steps {
                sh 'docker push vyshnavi2227doc/banking-project:v1'
            }
        }
    }
}
}
