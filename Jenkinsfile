pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/jaswanthbalaji/java-demo-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run') {
            steps {
                sh 'java -jar target/app.jar'
            }
        }
    }

    post {
        success { echo 'Build and run succeeded!' }
        failure { echo 'Build failed.' }
    }
}
