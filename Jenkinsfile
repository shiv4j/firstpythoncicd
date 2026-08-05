pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/shiv4j/firstpythoncicd.git'
            }
        }

        stage('Verify Python') {
            steps {
                bat 'python --version'
                bat 'pip --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'python -m pip install --upgrade pip'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m unittest discover'
            }
        }

        stage('Run Application') {
            steps {
                bat 'python calculator.py'
            }
        }
    }

    post {
        success {
            echo 'Build Successful'
        }
        failure {
            echo 'Build Failed'
        }
        always {
            echo 'Pipeline Finished'
        }
    }
}