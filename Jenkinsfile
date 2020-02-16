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
        KUBECTL_HELM_IMAGE_NAME = "kubectl-helm"
        KUBECTL_HELM_IMAGE_VERSION = "0.1"
        KUBECTL_HELM_IMAGE = "${DOCKER_REPO}:${KUBECTL_HELM_IMAGE_NAME}-${KUBECTL_HELM_IMAGE_VERSION}"
        AWS_REGION = "eu-west-1"
        DOCKER_TAG = "${DOCKER_REPO}:${DOCKER_IMAGE_NAME}-${DOCKER_IMAGE_VERSION}"
    } 
    stages {
        stage("context"){ 
               steps {
                sh '''
                  docker run -v /tmp/.kube:/root/.kube --rm ${KUBECTL_HELM_IMAGE} aws eks --region ${AWS_REGION} update-kubeconfig --name eks_demo_dev
                '''
               }
        }
        stage ("deploy"){
               steps { 
                sh '''
                  docker run -v /tmp/.kube:/root/.kube -v $(pwd)/deploy.yml:/tmp/deploy.yml --rm ${KUBECTL_HELM_IMAGE} kubectl apply -f /tmp/deploy.yml
                '''
               }
        }
        stage ("Check"){
               steps { 
                sh '''
                  count=7; 
                  while [ $(docker run -v /tmp/.kube:/root/.kube --rm ${KUBECTL_HELM_IMAGE} kubectl get pods -l app=apple-app -o 'jsonpath={..status.conditions[?(@.type=="Ready")].status}') != "True" -o $count -eq 0 ]; do 
                    echo "waiting for pod"
                    sleep 1
                    count=$((count - 1))
                  done
                '''
               }
        }
    }
}