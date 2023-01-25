pipeline {
    environment {
	DOCKERHUB_CREDENTIALS=credentials('dockerhub')
  }
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
     	 sh(
               script: "echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin",
               returnStatus: true
              )
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
