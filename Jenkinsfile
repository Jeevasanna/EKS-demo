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
        
//         stage('SonarQube analysis') {
//             steps{
//                 withSonarQubeEnv('sonar') { 
//                  sh "mvn clean package sonar:sonar"
//                 }
//             }
//        }
//        stage("Quality Gate") {
//             steps {
//               timeout(time: 1, unit: 'HOURS') {
//                 waitForQualityGate abortPipeline: true
//                 // in manage jenkins > configure systems > sonarqube servers > Url should not end with / it must be http//ip:9000
//               }
//             }
//           }
//           stage('Docker Build and Push') {
//       steps {
//       	withCredentials([usernamePassword(credentialsId: 'demo', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
//         	sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
//             sh 'chmod 777 automate.sh'
//             sh './automate.sh'
//         }
//       }
//            }
//              stage ("kubernetes deployment") {
//                 steps{
//                   sh 'kubectl apply -f deployment_demo.yml'
//                 }
//     }
         }
            
    }
