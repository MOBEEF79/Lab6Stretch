pipeline {
    agent any
    environment {
      DOCKER_CREDS = credentials('docker_creds')
    }    
    stages {
        stage('Build and deploy containers'){
            steps {
                sh "sh Deploy.sh"
            }
        }
        stage('Push containers'){
            steps {
                sh "echo $DOCKER_CREDS_PSW | docker login -u $DOCKER_CREDS_USR --password-stdin"
                sh "docker tag trio-task-flask-app:latest meauldflipflop/lab6stretch-app:latest"
                sh "docker tag trio-task-mysql:5.7 meauldflipflop/lab6stretch-db:latest"
                sh "docker push meauldflipflop/lab6stretch-app:latest"
                sh "docker push meauldflipflop/lab6stretch-db:latest"
            }
        }
    }
}