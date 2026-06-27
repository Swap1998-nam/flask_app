pipeline {
    agent any

    environment {
        IMAGE_NAME = "iamswapnil98/flask_app"
        IMAGE_TAG  = "v1"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
                }
            }
        }

        stage('Verify Image') {
            steps {
                sh "docker images | grep flask-devops"
            }
        }
    }

    post {
        success {
            echo 'Docker image built successfully.'
        }

        failure {
            echo 'Docker image build failed.'
        }

        always {
            echo 'Pipeline execution completed.'
        }
    }
}
```

