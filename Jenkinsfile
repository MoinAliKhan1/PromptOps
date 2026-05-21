pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/MoinAliKhan1/PromptOps.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building HTML project"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'cp index.html /usr/share/nginx/html/'
            }
        }
    }
}
