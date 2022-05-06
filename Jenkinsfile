pipeline {
   agent any
    stages {
        stage('setup') {            
            steps {
//                sh 'docker run neo4j:4.3'                
                sh 'pip --version'
                sh 'python --version'
                sh 'python -m venv venv'
                sh './venv/bin/activate && pip install kgx'
            }
        }
    }
}