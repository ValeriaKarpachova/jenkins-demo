pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'git@github.com:ValeriaKarpachova/jenkins-demo.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }

    post {
        success {
            emailext(
                to: 'xrd132006lera@gmail.com',
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """Збірка пройшла успішно.

Проєкт: ${env.JOB_NAME}
Номер збірки: ${env.BUILD_NUMBER}
Посилання: ${env.BUILD_URL}"""
            )
        }
        failure {
            emailext(
                to: 'xrd132006lera@gmail.com',
                subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """Збірка завершилась з помилкою!

Проєкт: ${env.JOB_NAME}
Номер збірки: ${env.BUILD_NUMBER}
Логи: ${env.BUILD_URL}console"""
            )
        }
    }
}