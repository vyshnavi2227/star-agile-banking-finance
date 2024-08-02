pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'vyshnavi2227doc/banking-project'
        DOCKER_TAG = 'v1'
    }
    
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
                withCredentials([string(credentialsId: 'docker_creds', variable: 'DOCKER_HUB_PASSWORD')]) {
                    sh 'echo $DOCKER_HUB_PASSWORD | docker login -u vyshnavi2227doc --password-stdin'
                }
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} .'
            }
        }
        stage('Docker Push') {
            steps {
                sh 'docker push ${DOCKER_IMAGE}:${DOCKER_TAG}'
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
