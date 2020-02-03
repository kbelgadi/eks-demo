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
                sh '''
                  export KUBECONFIG=/home/jenkins/.kube/config
                  kubectl version
                '''
                  // // sh 'kubectl version'
                  // sh "docker run -v /tmp/.kube:/root/.kube --rm kubectl-helm:0.1 kubectl version"
                }
        }
        stage ("Build"){
               steps { 
                sh '''
                  helm repo add stable https://kubernetes-charts.storage.googleapis.com
                  helm repo update
                  helm upgrade --install postgresql stable/postgresql --set persistence.enabled=false
                  export KUBECONFIG=/home/jenkins/.kube/config
                  kubectl get pods
                '''
                // sh 'kubectl version'
                //  sh "docker run -v /tmp/.kube:/root/.kube --rm kubectl-helm:0.1 helm version"
               }
        }
    }
}