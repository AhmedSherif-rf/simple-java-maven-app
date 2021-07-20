pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Build') {
            steps {
                script{
                    echo 'building the application'
                    sh 'mvn package'
                }  
            }
        }
        stage('build image') {
            steps {
                script{
                    echo 'building the docker image'ariable: 'PASS', username
                    withCredentials([usernamePassword(credentialsId: 'dockerhub-repo', passwordVariable: 'PASSWORD', usernameVariable: 'USER')]) {
                        sh 'docker build -t ahmedsherifmo/maven-app:mvn-2.0 .'
                        sh "echo $PASSWORD | docker login -u ${USER} --password-stdin"
                        sh 'docker push ahmedsherifmo/maven-app:mvn-2.0'
                    }
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
