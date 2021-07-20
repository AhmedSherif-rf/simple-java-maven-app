pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script{
                    echo 'building the application'
                }  
            }
        }
        stage('build image') {
            steps {
                script{
                    echo 'building the docker image'
                }
            }
        }
        stage('Deliver') {
            steps {
                script{
                   echo 'Deliver stage'
                }
            }
        }
    }
}
