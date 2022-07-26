pipeline {
  
  agent any
  environment {
        AWS_ACCOUNT_ID="255645000496"
        AWS_DEFAULT_REGION="ap-south-1" 
        IMAGE_REPO_NAME="jenkin-pipeline-build-demo"
        IMAGE_TAG="latest"
        REPOSITORY_URI = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}"
    }
 
  stages {
  
  stage('login into ecr') {
          
        steps 
        {
          sh "aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com"
          
        }
       }
      
     
   stage('Run Docker container on Jenkins Agent') {
             
         steps 
         {
             sh "docker run -d -p 3019:3000 rohitkhot10/nodejs"
 
          }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh 'ssh -v -o StrictHostKeyChecking=no  root@172.31.42.8 docker run -d -p 3019:3000 rohitkhot10/nodejs:latest'
 
            }
        }
    }
 }
