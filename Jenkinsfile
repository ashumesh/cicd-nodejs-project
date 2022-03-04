pipeline {
  
  agent any
 
  stages {
  
  stage('Pull image to Docker Hub') {
          
        steps 
        {
            sh  'docker pull rohitkhot10/nodejs:latest'
          
        }
       }
      
     
   stage('Run Docker container on Jenkins Agent') {
             
         steps 
         {
             sh "docker run -d -p 3000:3000 rohitkhot10/nodejs"
 
          }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh 'ssh root@172.31.42.8 docker run -d -p 3000:3000 rohitkhot10/nodejs:latest'
 
            }
        }
    }
 }
