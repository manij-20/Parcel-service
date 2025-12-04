pipeline {
    agent { label 'java' }

    tools {
        jdk 'JDK17'
        maven 'maven'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm     
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests=false'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Run Application') {
            steps {
                sh 'mvn spring-boot:run &'
            }
        }
    }
}
