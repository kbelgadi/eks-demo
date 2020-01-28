pipeline {
    agent any
    stages {
        stage("Prepare"){
               steps{
                 sh '''
                   echo "Prepare continuous delivery env"
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