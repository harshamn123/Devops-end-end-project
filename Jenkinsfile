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
                sh 'sudo docker build -t harshamn8/webapp1:latest .'
            }
        }

        stage('Docker Push') {

            steps {
                sh 'sudo docker push harshamn8/webapp1:latest'
            }
        }

        stage('Kubernetes Deploy') {

            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
        stage('expose port'){
            steps{
                sh 'kubectl port-forward service/webapp-service 9090:8080 --address 0.0.0.0'
        }
    }
}
}
