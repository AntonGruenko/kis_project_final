pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {

        stage('Checkout Code') {
            steps {
                cleanWs()
                checkout scm
            }
        }

        stage('Docker Deploy') {
            steps {
                echo 'Перезапускаем контейнеры команды project_01...'
                sh 'docker compose -p project_01 down'
                sh 'docker compose -p project_01 up -d --build'
            }
        }
    }
}
