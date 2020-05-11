pipeline {
    agent any
        echo 'Started'
        stage('GIT Checkout') 
        {
            git 'https://github.com/shantanuchandalia/simple-java-maven-app.git'
        }
        stage('Execute') 
        {
            bat label: '', script: 'mvn clean package' 
            input 'Should this be archieved?'
        }  
        stage('Archive') 
        {
            step([$class: 'JUnitResultArchiver', testResults: 'target/surefire-reports/TEST-*.xml'])
            archiveArtifacts 'target/*.jar'
        }
        echo 'Success'
}
