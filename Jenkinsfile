pipeline {
   agent any
    stages {
        stage('setup') {            
            steps {
//                sh 'docker run neo4j:4.3'                
                sh 'pip --version'
                sh 'python3 --version'
                sh 'python3 -m venv venv'
                sh './venv/bin/activate && pip install kgx'
            }
        }
    }
}