pipeline {
    agent { docker { image 'kubectl-helm:0.2' } }
    stages {
        stage("Prepare"){
               steps{
                  sh '''
                   echo "Prepare continuous delivery env"
                   '''
                    // run your command
                    aws eks --region eu-west-1 update-kubeconfig --name eks_demo_dev
                    kubectl get no
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