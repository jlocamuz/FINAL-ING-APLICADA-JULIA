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
                sh "npm install cypress --save-dev --ignore-scripts"
                sh "npm i --ignore-scripts"
                sh "./node_modules/.bin/cypress run"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }}
