pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install --ignore-scripts'
                sh 'mvn -B -DskipTests clean package'
                }
            

            }
        stage('Test') {
            steps {
                sh " mvn test -Dtest=MyTest"
                sh "npm install cypress@latest --save-de"
                sh "./node_modules/.bin/cypress run"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }}
