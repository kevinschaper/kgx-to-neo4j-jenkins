pipeline {
   agent any
    stages {
        stage('setup') {            
            steps {
                sh 'docker info'                
                sh 'pip --version'
            }
        }
    }
}