pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo "Fetching code from GitHub"
                git branch: "${env.BRANCH_NAME}",
                    url: 'https://github.com/Varun85535/multibranch.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building application"
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests"
                sh 'mvn test'
            }
        }

        stage('Run') {
            steps {
                echo "Running application"
                sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.example.App'
            }
        }
    }

    post {
        success {
            echo "Pipeline SUCCESS for branch: ${env.BRANCH_NAME}"
        }
        failure {
            echo "Pipeline FAILED"
        }
    }
}
