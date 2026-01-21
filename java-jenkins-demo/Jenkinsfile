pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/dossvenkat1972/java-jenkins-demo.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                bat 'xcopy target\\*.jar C:\\deploy\\ /Y'
            }
        }
    }

    post {
        success {
            echo "✅ Build & Deployment Successful"
        }
        failure {
            echo "❌ Build Failed"
        }
    }
}
