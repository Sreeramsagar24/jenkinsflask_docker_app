pipeline {
    agent any

    stages {

        stage("checkout") {
            steps {
                echo "========executing checkout========"
                checkout scm
            }
        }

        stage("setup environment") {
            steps {
                echo "========executing settingup environment========"

                bat '''
                python -m venv .venv1
                .venv1\\Scripts\\pip install -r requirements.txt
                '''
            }
        }

        stage("run tests") {
            steps {
                bat '''
                echo "========executing unittests========"
                .venv1\\Scripts\\pytest tests/
                '''
            }
        }

        stage("Deploy") {
            steps {
                bat '''
                echo "========deploying========"
                start /B .venv1\\Scripts\\python app.py
                '''
            }
        }
    }
}