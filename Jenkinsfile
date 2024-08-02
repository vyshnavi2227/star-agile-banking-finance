pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/vyshnavi2227/star-agile-banking-finance.git'
                 echo 'github url checkout'
            }
        }
        stage('vyshnavi codecompile'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('vyshnavi codetesting'){
            steps{
                sh 'mvn test'
            }
        }
        stage('vyshnavi qa'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c01 myimg'
            }
        }   
    }
}
