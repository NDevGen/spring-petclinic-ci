pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1'
        jdk 'Java 11'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/NdevGen/spring-petclinic-ci.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t spring-petclinic .'
            }
        }
    }
}
