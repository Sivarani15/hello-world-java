pipeline {
    agent{
        label 'JAVA11'
    }
    stages{
        stage ('Source code') {
            steps {
                git branch: 'master', url: 'https://github.com/Sivarani15/hello-world-java.git'
            }

        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Sonarqubeanlysis') {
            steps {
                withSonarQubeEnv('SONAR_LATEST') {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
        stage('Archiving Artifacts') {
            steps {
                junit testResults: 'target/surefire-reports/*.xml'
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }
} 