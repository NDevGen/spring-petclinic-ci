pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1'
        jdk 'Java 11'
    }

    stages {
        stage('Checkout') {
            steps {
        git branch: 'main', url: 'https://github.com/NdevGen/spring-petclinic-ci.git'
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
                script {
                    dockerImage = docker.build("spring-petclinic:latest")
                }
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:8080 --name petclinic spring-petclinic:latest'
            }
        }
    }
}
