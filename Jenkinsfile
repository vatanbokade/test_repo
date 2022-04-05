pipeline {
  agent any
  
  stages {
        
    stage('Git') {
      steps {
        git branch: 'mediaagility', credentialsId: 'gitlabsuchita', url: 'https://gitlab.extramarks.com/root/newapigateway.git'
      }
    }
         
    stage('Build Docker image'){
          steps{
               
               sh 'docker build -t asia-south1-docker.pkg.dev/em-uat/extramarks/newapigateway/dev:${BUILD_NUMBER} -f Dockerfile-dev .'
          }
      }
    
    stage('Docker push to Artifact Registry')
    {       steps{
                sh 'gcloud auth configure-docker asia-south1-docker.pkg.dev --quiet'
                sh 'docker push asia-south1-docker.pkg.dev/em-uat/extramarks/newapigateway/dev:${BUILD_NUMBER}'
           }
    
       }
    //  stage('Updating tag')
   // {       steps{
     //           sh 'sed -i "s!currenttag!${BUILD_NUMBER}!g" k8s-dev/deployment.yaml '
               
       //    }
    
       //}

         // stage('Deploy Staging') {
           // steps{

             // sh 'gcloud container clusters get-credentials em-devuat-gke-cluster01 --zone asia-south1-a --project em-uat'
             // sh 'kubectl apply -f k8s-dev/'
                
            //}
        //} 
    
}
}
  }
}
