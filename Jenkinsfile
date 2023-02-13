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
                //sh "rm -rf node_modules package-lock.json"
                sh " mvn test -Dtest=MyTest"
                //sh "npm install --ignore-scripts"
                //sh "npm install cypress --save --ignore-scripts"
                //sh "./node_modules/.bin/cypress run"
            }
        }
        stage('publish docker') {
            steps{
                withDockerRegistry([ credentialsId: "dockerhubaccount", url: 'https://hub.docker.com/app:latest']) {
                script {
                    dockerImage.push()
                    }
               
                }
        }

    }
    }
}