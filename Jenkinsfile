
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/bazzi777/jenkins-web-deployment.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building website...'
                sh 'ls -l index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website to Apache...'
                sh '''
                    sudo -n /usr/bin/install -m 0644 /var/lib/jenkins/workspace/Pipeline-Web-Deployment/index.html /var/www/html/index.html
                '''
                echo 'Website deployed successfully!'
            }
        }

        stage('Verify') {
            steps {
                echo 'Verifying website...'
                sh 'curl -f http://127.0.0.1/'
            }
        }
    }
}

