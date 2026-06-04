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
                sh 'pyflakes3 "expense tracker.py"'
                echo 'Lint passed!'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t expense-tracker:${BUILD_NUMBER} .' 
                echo 'Docker image built!'
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
