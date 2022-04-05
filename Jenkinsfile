pipeline {
  agent any
  
  stages {
        
    stage('Git') {
      steps {
        git branch: 'main', url: 'https://github.com/vatanbokade/test_repo.git'
      }
    }
  

         
  
    // stage('Docker push to Artifact Registry')
    // {       steps{
    //             sh 'gcloud auth configure-docker asia-south1-docker.pkg.dev --quiet'
    //             sh 'docker push asia-south1-docker.pkg.dev/em-uat/extramarks/newapigateway/dev:${BUILD_NUMBER}'
    //        }
    
    //    }
    //  stage('Updating tag')
   // {       steps{
     //           sh 'sed -i "s!currenttag!${BUILD_NUMBER}!g" k8s-dev/deployment.yaml '
               
       //    }
    
       //}

         stage('Deploy Staging') {
            steps{

              sh 'gcloud container clusters get-credentials cluster-vatan --zone asia-south1 --project business-transformers'
              sh 'kubectl apply -f k8s/'
                
            }
        }
}
}
