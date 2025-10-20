pipeline {
    agent any
    
    tools{
        maven 'Maven-3.9.11'
    }
    stages {
        stage('clone') {
            steps {
              git 'https://github.com/satapriya04/test-maven-webapp.git'
            }
        }
        stage('Maven build'){
            steps{
                 sh 'mvn clean package'
            }
        }
        stage('docker image'){
            steps {
                sh 'docker build -t ashokit/mavenwebapp .'
            }
        }
        stage('k8s deploy'){
            steps{
               sh 'kubectl apply -f k8s-deploy.yml'
            }
        }
    }
}
