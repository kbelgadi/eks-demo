pipeline {
    agent any
    stages {
        stage("Prepare"){
               steps{
                  sh '''
                   echo "Prepare continuous delivery env"
                   
                    aws eks --region eu-west-1 update-kubeconfig --name eks_demo_dev
                    kubectl get no
                    docker run --rm -v $HOME/.kube:/root/.kube kubectl-helm:0.2 kubectl get no
                  '''
                }
        }
        stage ("Build"){
               steps {
                 sh '''
                   echo "Building app"
                 '''
               }
        }
    }
}