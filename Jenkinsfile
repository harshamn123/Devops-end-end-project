pipeline {

    agent any

    stages {

        stage('Checkout') {

            steps {
                checkout scm
            }
        }

        stage('Build Maven') {

            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {

            steps {
                sh 'docker build -t harshamn8/webapp:latest .'
            }
        }

        stage('Docker Push') {

            steps {
                sh 'docker push harshamn8/webapp:latest'
            }
        }

        stage('Kubernetes Deploy') {

            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
