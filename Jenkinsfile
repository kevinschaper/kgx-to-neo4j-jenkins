pipeline {
   agent any
    stages {
        stage('setup') {            
            steps {
                sh 'docker run --name neo -p7474:7474 -p7687:7687 -d --env NEO4J_AUTH=neo4j/admin neo4j:3.4.15'
                sh 'pip --version'
                sh 'python3 --version'
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate'
                sh './venv/bin/pip install kgx'
            }
        }
        stage('download') {
            steps {
                sh 'gsutil cp gs://monarch-ingest/latest/monarch-kg.tar.gz .'
            }
        }
        stage('transform') {
            steps {
                sh './venv/bin/kgx transform --transform-config transform.yaml'
            }
        }
        stage('package') {
            steps {
                sh 'docker cp neo:/data .'
                sh 'tar czf neo4j.tar.gz data'
            }
        }
        stage('upload') {
            steps {
                sh 'gsutil cp neo4j.tar.gz gs://monarch-ingest/latest/'
            }
        }
    }
}