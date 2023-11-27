pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/your-username/your-html-project.git'
        NGINX_PATH = 'C:\\path\\to\\nginx\\html'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Ensure you have Git installed and available in the PATH
                    bat "git clone --branch main --single-branch %GIT_REPO_URL%"
                }
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    // Assuming your HTML project is in a subdirectory named 'your-html-project'
                    bat "xcopy /s /y .\\your-html-project\\* %NGINX_PATH%"
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! You can add additional steps here.'
        }
        failure {
            echo 'Pipeline failed! You may want to take some actions.'
        }
    }
}
