pipeline {
    agent any   ## node ('Testserver1') {}
    stages {
        stage ('SCM for Java code')  {
            steps {
                git branch: 'main', url: 'https://github.com/jjz2021/cicdMavenJunit.git'
                echo 'Polling to Developers SCM'
            }
            
        }
        stage ('Maven Compile' ) {
            steps{
                sh '''mvn clean
                        mvn compile'''
                 echo 'Compiling . . . '
            }
            
        }
        stage ('Testing code') {
            steps{
                sh 'mvn test'
                echo 'Testing comlete with Junit on maven. . . '
            }
        }
        
        stage ('Package') {
            steps{
                sh 'mvn package'
                echo 'Packaging . . . '
            }
            
        }
        stage ('Publish Test results') {
            steps{
                junit 'target/surefire-reports/*.xml'
            }
            
        }
        stage ('Execute Jar file') {
            steps {
                sh 'java -jar target/*.jar'
            }
            
        }
    }
}
