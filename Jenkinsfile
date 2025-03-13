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
                    // Compile main.cpp
                    sh 'g++ ${FILE_NAME} -o ${BUILD_NAME}'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run the compiled program
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
