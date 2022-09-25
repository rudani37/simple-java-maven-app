pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    tools {
    maven 'M3'
    }
    stages {
    stage('init') {
        checkout scm
    }
     stages {
        stage('Build') {
            steps {
                container ('maven'){
                  sh 'mvn version'
                }
            }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
