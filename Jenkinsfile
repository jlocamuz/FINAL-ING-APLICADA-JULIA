node {
    
    stage('./mvn') {
        sh 'mvn -B -DskipTests clean package'

    }
    stage('npm install') {
        sh "./mvnw -ntp com.github.eirslett:frontend-maven-plugin:npm"
    }
    stage('backend tests') {
       try {
            sh " mvn test -Dtest=MyTest"

       } catch(err) {
           throw err
       }
    }

    stage('frontend tests') {
       try {
           sh "./mvnw -ntp com.github.eirslett:frontend-maven-plugin:npm -Dfrontend.npm.arguments='run test'"
       } catch(err) {
           throw err
       } finally {
           sh "./node_modules/.bin/cypress run"
       }
    }

    stage('packaging') {
        sh "./mvnw -ntp verify -P-webapp -Pprod -DskipTests"
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
    }

    def dockerImage
    stage('publish docker') {
        // A pre-requisite to this step is to setup authentication to the docker registry
        // https://github.com/GoogleContainerTools/jib/tree/master/jib-maven-plugin#authentication-methods
        //sh "./mvnw -ntp -Pprod verify jib:build"
        withCredentials([usernamePassword(credentialsId: 'dockerhubaccount', passwordVariable: 'DOCKER_REGISTRY_PWD', usernameVariable: 'DOCKER_REGISTRY_USER')]) {
            sh "./mvnw -ntp jib:build"
        }
    
    }
}