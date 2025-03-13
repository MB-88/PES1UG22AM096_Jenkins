pipeline {
    agent any

    environment {
        REPO_URL = 'your-repo-url'
        FILE_NAME = 'main.cpp'
        BUILD_NAME = 'YOUR_SRN-1'
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    sh 'git clone ${REPO_URL} repo'
                    sh 'cd repo && touch ${FILE_NAME}'
                    sh 'echo "#include <iostream>\nusing namespace std;\nint main() { cout << \"Hello, World!\" << endl; return 0; }" > repo/${FILE_NAME}'
                    sh 'cd repo && git add ${FILE_NAME} && git commit -m "Added main.cpp" && git push'
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
