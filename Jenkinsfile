pipeline {
    agent any

    environment {
        FILE_NAME = 'main.cpp'
        BUILD_NAME = 'PES1UG22AM096-1'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'g++ ${FILE_NAME} -o ${BUILD_NAME}'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './${BUILD_NAME}'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
