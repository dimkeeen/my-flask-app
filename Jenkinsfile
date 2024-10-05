pipeline {
    agent any 

    stages {
        stage('Clone') {
            steps {
                // Клонирование репозитория
                git url: 'https://github.com/dimkeeen/my-flask-app.git'
            }
        }
        stage('Build') {
            steps {
                // Сборка проекта (например, установка зависимостей)
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                // Запуск тестов
                sh 'pytest'
            }
        }
        stage('Deploy') {
            steps {
                // Развертывание приложения
                sh 'docker build -t my-flask-app .'
                sh 'docker run -d -p 5000:5000 my-flask-app'
            }
        }
    }
}
