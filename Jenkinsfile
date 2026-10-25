pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Sirivalli-1010/python-cicd.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Compile') {
            steps {
                bat 'python -m compileall -q app.py test_app.py'
            }
        }

        stage('Test') {
            steps {
                bat 'python -m pytest -v'
            }
        }

        stage('Package') {
            steps {
                bat 'python -c "import zipfile; z=zipfile.ZipFile(\'python-app.zip\', \'w\', zipfile.ZIP_DEFLATED); z.write(\'app.py\'); z.close()"'
                archiveArtifacts artifacts: 'python-app.zip',
                                 fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Python CI/CD pipeline completed successfully!'
        }

        failure {
            echo 'Python CI/CD pipeline failed. Check the console output.'
        }
    }
}