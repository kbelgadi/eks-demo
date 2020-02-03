pipeline {
    agent {
      docker { 
        image 'kubectl-helm:0.1' 
        args '-v /tmp/.kube:/home/jenkins/.kube'
      }
    }
    // agent any    
    stages {
        stage("Prepare"){ 
               steps{
                  sh 'ls /'
                  // // sh 'kubectl version'
                  // sh "docker run -v /tmp/.kube:/root/.kube --rm kubectl-helm:0.1 kubectl version"
                }
        }
        stage ("Build"){
               steps { 
                sh '''
                  KUBECONFIG=/home/jenkins/.kube
                  kubectl version
                '''
                // sh 'kubectl version'
                //  sh "docker run -v /tmp/.kube:/root/.kube --rm kubectl-helm:0.1 helm version"
               }
        }
    }
}