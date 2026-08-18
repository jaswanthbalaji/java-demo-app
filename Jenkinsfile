pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/jaswanthbalaji/java-demo-app.git'
            }
        }
        stage('Build Jar') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t java-demo-app:latest .'
            }
        }
        stage('Run Container') {
            steps {
                sh '''
                    docker stop java-demo-app || true
                    docker rm java-demo-app || true
                    docker run -d --name java-demo-app java-demo-app:latest
                '''
            }
        }
    }

    post {
        success { echo 'Docker build and container run succeeded!' }
        failure { echo 'Build failed.' }
    }
}
