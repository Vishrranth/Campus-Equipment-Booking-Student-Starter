pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code is available in the workspace.'
            }
        }

        stage('Build and Test') {
            steps {
                sh 'mvn clean test package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t campus-equipment-booking:set-b .'
            }
        }
    }
}
