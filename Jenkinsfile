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
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
