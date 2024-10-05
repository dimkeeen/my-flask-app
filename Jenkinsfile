pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                // Клонируем репозиторий
                git url: 'https://github.com/dimkeeen/my-flask-app.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                . venv/bin/activate
                python -m unittest discover
                '''
            }
        }

        stage('Run Application') {
            steps {
                sh '''
                . venv/bin/activate
                flask run
                '''
            }
        }
    }

    post {
        always {
            // Cleanup
            sh 'rm -rf venv'
        }
    }
}