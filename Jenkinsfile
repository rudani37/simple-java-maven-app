node { 
    stage('Test') {
       sh 'mvn test'
       junit 'target/surefire-reports/*.xml'
    }
    stage('Build') {
        sh 'mvn -B -DskipTests clean package'
    }
    stage('Deliver') {
        sh './jenkins/scripts/deliver.sh'
    }
}