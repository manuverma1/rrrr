pipeline {
    agent any    
    stages {
    // Docker build
    stage('Docker Build') {
      steps{
        script {
          dockerImage = docker.build("063556473257.dkr.ecr.us-east-1.amazonaws.com/pakshirepo:$BUILD_ID", ".")
        }
      }
    }
     // Uploading Docker images into Docker Hub
    stage('Pushing to ECR') {
     steps{  
         script {
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 063556473257.dkr.ecr.us-east-1.amazonaws.com'
                sh 'docker push 063556473257.dkr.ecr.us-east-1.amazonaws.com/pakshirepo:$BUILD_ID'
         }
        }
      }
    }
}
