pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/anjanaviswa/Banking-java-project/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with anjana'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with anjana'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with anjana'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with anjana'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t anjanaviswa/project_bankingandfinance:v1 .'
           }
         }

        stage('Login to docker hub and push the file'){
          steps{
              withCredentials([string(credentialsId: 'dockerhubpass', variable: 'dockerhubpass')]) {
                  sh 'docker login -u anjanaviswa -p ${dockerhubpass}'
                 }
          }

              
    }
}
