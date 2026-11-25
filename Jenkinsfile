pipeline {
    agent any
    environment {
        DH_USER = 'kadrighoffrane'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kghoffrane-debug/MyAppReact.git'
            }
        }
        stage('Build images') {
            steps {
                sh 'docker build -t $DH_USER/mern-server:latest ./Server'
                sh 'docker build -t $DH_USER/mern-client:latest ./Client'
            }
        }
        stage('Push Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'U', passwordVariable: 'P')]) {
                    sh 'echo $P | docker login -u $U --password-stdin'
                    sh 'docker push $DH_USER/mern-server:latest'
                    sh 'docker push $DH_USER/mern-client:latest'
                }
            }
        }
    }
}
