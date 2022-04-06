pipeline {
  agent any
  
  stages {
        
    stage('Git') {
      steps {
        git branch: 'main', url: 'https://github.com/vatanbokade/test_repo.git'
      }
    }
  stage('Build') {
      steps {
        sh 'echo "Build Successful"'
      }
    }
    
    stage('Test') {
      steps {
        sh 'echo "Test Successful"'
      }
    }

         
          stage('Deploy Staging') {
            steps{

              sh 'gcloud container clusters get-credentials cluster-vatan --zone asia-south1 --project business-transformers'
              sh 'kubectl apply -f k8s/deployment.yaml'
                
            }
        }
}
}
