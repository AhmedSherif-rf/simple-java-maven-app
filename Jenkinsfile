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
                    withCredentials([usernamePassword(credentialsId: 'dockerhub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]){
                        sh 'docker build -t ahmedsherifmo/maven-app:mvn-2.0 .'
                        sh "echo ${PASS} | docker login -u ${USER} --password-stdin"
                        sh 'docker push ahmedsherifmo/maven-app:mvn-2.0'
                    }
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
