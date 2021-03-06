pipeline {
    agent {
        docker { image '897964440075.dkr.ecr.eu-west-1.amazonaws.com/ecr_demo_dev:kubectl-helm-0.1' }
    }
    environment {
        EKS_NAME = "eks-demo-dev"
        AWS_REGION = "eu-west-1"
        KUBECONFIG="/tmp/config"
    }     
    stages {
        stage('context') {
            steps {
                sh '''
                  aws eks --region ${AWS_REGION} update-kubeconfig --name ${EKS_NAME}
                '''
            }
        }
        stage ("deploy"){
               steps { 
                sh '''
                  kubectl apply -f deploy.yml
                '''
               }
        }
        stage ("check"){
               steps { 
                sh '''
                  count=7; 
                  while [ $(kubectl get pods -l app=apple-app -o 'jsonpath={..status.conditions[?(@.type=="Ready")].status}') != "True" -o $count -eq 0 ]; do 
                    echo "waiting for pod"
                    sleep 1
                    count=$((count - 1))
                  done
                '''
               }
        }
        stage ("service"){
               steps { 
                sh '''
                  kubectl apply -f service.yml
                '''
               }
        }
        stage ("ingress"){
               steps { 
                sh '''
                  kubectl apply -f ingress.yml
                '''
               }
        }
    }
}