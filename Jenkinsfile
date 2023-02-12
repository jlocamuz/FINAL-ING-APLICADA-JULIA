pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install --ignore-scripts'
                }

            }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }}
