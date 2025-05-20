pipeline {
    agent any

    tools {
        maven 'Maven 3'   // Make sure you have this Maven tool configured in Jenkins
        jdk 'Java 17'     // Or Java 11/21 — match your project
    }

    environment {
        PROJECT_NAME = 'java-gitops-sample'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/YOUR_USERNAME/YOUR_REPO.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project with Maven...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
