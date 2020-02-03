pipeline {
    agent any {
      docker { image 'kubectl-helm:0.1' }
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