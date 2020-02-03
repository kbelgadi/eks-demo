pipeline {
    agent {
      docker { 
        image 'kubectl-helm:0.1' 
        args '-v /tmp/.kube:/root/.kube'
      }
    }
    
    stages {
        stage("Prepare"){ 
               steps{
                  sh 'kubectl version'
                }
        }
        stage ("Build"){
               steps {
                 sh 'helm version'
               }
        }
    }
}