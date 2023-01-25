pipeline {
    agent any
    
    stages{
       stage('checkout code'){
            steps{
                git branch: 'main', url: 'https://github.com/Jeevasanna/EKS-demo.git'
            }
         }        
       stage('Build Artifact'){
            steps{
                sh 'mvn clean install'
            }
        }
        

          stage('Docker Build and Push') {
      steps {
      	withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        	sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
            sh '''
             docker build -t vijay-demo .
             docker tag vijay-demo jeevavijayanand/sanna:latest
             docker push jeevavijayanand/sanna:latest
             '''
        }
      }
           }
//              stage ("kubernetes deployment") {
//                 steps{
//                   sh 'kubectl apply -f deployment.yml'
//                 }
//     }
         }
            
    }
