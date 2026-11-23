pipeline {

    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Application'
                sh 'ls -la'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Creating Docker Image'
                sh 'docker build -t jenkins-demo:latest .'
            }
        }

        stage('Verify') {
            steps {
                sh 'docker images'
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESSFUL'
        }

        failure {
            echo 'BUILD FAILED'
        }
    }
}
