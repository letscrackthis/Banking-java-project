pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/letscrackthis/Banking-java-project/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with darshan'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with darshan'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with darshan'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with darshan'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('Login to docker hub and push the file'){
            steps{
                withCredentials([string(credentialsId: 'dockerhubpass', variable: 'dockerhubpass')]) {
                sh 'docker login -u darshan200122 -p $(dockerhubpass}'
            }
        }   
    }
}
