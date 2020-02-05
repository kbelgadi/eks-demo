def buildimage = docker.image('buildimage:latest');

pipeline {
    // agent {
    //   docker { 
    //     image 'kubectl-helm:0.1' 
    //     withRun '-u root'
    //     args '-v /tmp/.kube:/home/jenkins/.kube'
    //   }
    // }
    agent any    
    stages {
        stage("Prepare"){ 
              // agent {
              //   docker { 
              //     image 'kubectl-helm:0.1' 
              //     args '-u root -v /tmp/.kube:/root/.kube'
              //   }
              // }                // sh '''
                //   export KUBECONFIG=/home/jenkins/.kube/config
                //   kubectl version
                // '''
                  // // sh 'kubectl version'
                  // sh "docker run -v /tmp/.kube:/root/.kube --rm kubectl-helm:0.1 kubectl version"
               
               steps {
                //  sh '''
                //     export KUBECONFIG=/root/.kube/config
                //     kubectl version
                //  '''
                sh '''
                  echo hello
                  eval $(/usr/local/bin/aws ecr get-login --registry-ids 897964440075 --no-include-email --region eu-west-1)
                '''
               }
        }
        stage ("Build"){
               steps { 
                sh '''
                  echo hello
                  ls
                  docker build -t alpine:0.1 .
                '''
                // sh '''
                //   echo hello
                //   helm repo add stable https://kubernetes-charts.storage.googleapis.com
                //   helm repo update
                //   helm upgrade --install postgresql stable/postgresql --set persistence.enabled=false
                //   export KUBECONFIG=/home/jenkins/.kube/config
                //   kubectl get pods
                // '''
                // sh 'kubectl version'
                //  sh "docker run -v /tmp/.kube:/root/.kube --rm kubectl-helm:0.1 helm version"
               }
        }
        stage ("Push"){
               steps { 
                sh '''
                  docker push 897964440075.dkr.ecr.eu-west-1.amazonaws.com/ecr_demo_dev:alpine-0.1
                '''
                // sh 'kubectl version'
                //  sh "docker run -v /tmp/.kube:/root/.kube --rm kubectl-helm:0.1 helm version"
               }
        }
    }
}