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
    environment {
        EKS_NAME = "eks_demo_dev"
        DOCKER_REPO = "897964440075.dkr.ecr.eu-west-1.amazonaws.com/ecr_demo_dev"
        KUBECTL_HELM_IMAGE_NAME = "helm-demo"
        KUBECTL_HELM_IMAGE_VERSION = "0.1"
        KUBECTL_HELM_IMAGE = "${DOCKER_REPO}:${KUBECTL_HELM_IMAGE_NAME}-${KUBECTL_HELM_IMAGE_VERSION}"
        AWS_ACCOUNT = "897964440075"
        AWS_REGION = "eu-west-1"
        DOCKER_TAG = "${DOCKER_REPO}:${DOCKER_IMAGE_NAME}-${DOCKER_IMAGE_VERSION}"
    } 
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
                  docker run -v /tmp/.kube:/root/.kube --rm 897964440075.dkr.ecr.eu-west-1.amazonaws.com/ecr_demo_dev:helm-demo-0.1 aws eks --region eu-west-1 update-kubeconfig --name eks_demo_dev
                '''
               }
        }
        stage ("Build"){
               steps { 
                sh '''
                  echo hello
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
                  echo hello
                '''
                // sh 'kubectl version'
                //  sh "docker run -v /tmp/.kube:/root/.kube --rm kubectl-helm:0.1 helm version"
               }
        }
    }
}