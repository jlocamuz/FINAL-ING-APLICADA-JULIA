pipeline {
    agent any
    tools {
        maven '3.6.3'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm i'
                sh 'mvn -B -DskipTests clean package'
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
