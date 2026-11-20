
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building web application...'
                sh 'test -f index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website to Apache...'
                sh 'sudo /usr/bin/install -m 0644 index.html /var/www/html/index.html'
            }
        }

        stage('Verify') {
            steps {
                echo 'Verifying deployment...'
                sh 'curl -fsS http://127.0.0.1/ | grep "Version 2"'
            }
        }
    }
}

