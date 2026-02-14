pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "2022bcs0095praneeth/wine-quality-api"
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
    }

    stages {

        stage('Train Model & Print Metrics') {
            steps {
                sh '''
                echo "=================================="
                echo "Name: P Sai Praneeth Kumar"
                echo "Roll No: 2022BCS0095"
                echo "=================================="
                python3 train.py
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh '''
                echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin
                docker push $DOCKER_IMAGE
                '''
            }
        }
    }
}
