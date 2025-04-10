pipeline {
    agent any

    environment {
        IMAGE_NAME = "anushreegm12/java-microservice"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Anushreegm12/java-maven.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests=false'
            }
        }

         stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                echo "sonarqube"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t anushreegm12/java-microservice .'
            }
        }
        stage('Push to DockerHub') {
            steps {
                echo "sonarqube"
                }
            }
        stage('Deploy to Kubernetes') {
            steps {
                sh """
                kubectl apply -f k8s/deployment.yaml
                kubectl apply -f k8s/service.yaml
                """
            }
        }
    }
}
