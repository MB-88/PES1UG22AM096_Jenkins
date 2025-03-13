pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/MB-88/PES1UG22AM096_Jenkins'
        FILE_NAME = 'main.cpp'
        BUILD_NAME = 'PES1UG22AM096-1'
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    sh 'git clone ${REPO_URL} repo'
                    sh 'cd repo && git config user.email "mohith.b88@gmail.com"'
                    sh 'cd repo && git config user.name "Mohith Bharath"'
                    sh 'cd repo && touch ${FILE_NAME}'
                    sh 'echo \"#include <iostream>\\nusing namespace std;\\nint main() { cout << \\\"Hello, World!\\\" << endl; return 0; }\" > repo/${FILE_NAME}'
                    sh 'cd repo && git add ${FILE_NAME} && git commit -m \"Added main.cpp\"'
                    sh 'cd repo && git push'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'g++ repo/${FILE_NAME} -o repo/${BUILD_NAME}'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './repo/${BUILD_NAME}'
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
