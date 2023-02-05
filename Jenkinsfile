pipeline {
    agent any
    stages {
        stage("Build Docker Image") {
            steps {
                sh "docker build -t helloworld ."
            }
        }
        stage("Run Docker Container") {
            steps {
                sh "docker run -d -p 5000:80 helloworld"
            }
        }
        stage("Deploy to Kubernetes") {
            steps {
                sh "kubectl create ns helloworld"
                sh "kubectl apply -f helloworld-deployment.yaml --namespace=helloworld"
                sh "kubectl create -f helloworld-service.yaml --namespace=helloworld"
            }
        }
    }
}
