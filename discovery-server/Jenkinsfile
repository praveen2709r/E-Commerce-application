pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                dir('discovery-server') {
                    bat 'mvn test'
                }
            }
        }

        stage('Build JAR') {
            steps {
                dir('discovery-server') {
                    bat 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('discovery-server') {
                    bat 'docker build -t discovery-server:1.0 .'
                }
            }
        }
    }
}