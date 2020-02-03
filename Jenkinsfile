pipeline {
    agent {
      docker { 
        image 'kubectl-helm:0.1' 
        args '-v /tmp/.kube:/home/jenkins/.kube'
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