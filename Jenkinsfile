pipeline {
    agent any
    
    tools{
        maven 'Maven-3.9.11'
    }
    stages {
        stage('clone') {
            steps {
              git 'https://github.com/alsiddiq901/maven-web-app.git'
            }
        }
        stage('build'){
            steps{
                 sh 'mvn clean package'
            }
        }
        stage('docker image'){
            steps {
                sh 'docker build -t alsiddiq/mavenwebapp .'
            }
        }
        stage('k8s deploy'){
            steps{
               sh 'kubectl apply -f k8s-deploy.yml'
            }
        }
    }
}
