pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Sheethal29/Expense-Tracker.git'
            }
        }

        stage('Verify Python') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Syntax Check') {
            steps {
                sh 'python3 -m py_compile "expense tracker.py"'
                echo 'Syntax check passed!'
            }
        }

        stage('Lint') {
            steps {
                sh 'pip3 install pyflakes --quiet'
                sh 'python3 -m pyflakes "expense tracker.py"'
            }
        }

    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed — check the logs above.'
        }
    }
}
