pipeline {
    agent {
        label 'master'
    }

    stages {

        stage('Setup') {
            steps {
                sh "pip3 install -r lambda-app/tests/requirements.txt"
            }
        }
        stage('Test') {
            steps {
                sh "pytest"
            }
        }

        stage('Build') {
            steps {
                sh "sam build -t lambda-app/template.yaml"

            }
        }
        stage('Deploy') {
            
            steps {
                sh "sam deploy -t lambda-app/template.yaml --no-confirm-changeset --no-fail-on-empty-changeset"

            }
        }
      
    }
}