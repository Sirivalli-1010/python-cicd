```groovy
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
                bat '"C:/Users/Siri/AppData/Local/Programs/Python/Python310/python.exe" -m pip install -r requirements.txt'
            }
        }

        stage('Compile') {
            steps {
                bat '"C:/Users/Siri/AppData/Local/Programs/Python/Python310/python.exe" -m compileall -q app.py test_app.py'
            }
        }

        stage('Test') {
            steps {
                bat '"C:/Users/Siri/AppData/Local/Programs/Python/Python310/python.exe" -m pytest -v'
            }
        }

        stage('Package') {
            steps {
                bat '"C:/Users/Siri/AppData/Local/Programs/Python/Python310/python.exe" -c "import zipfile; z=zipfile.ZipFile(\'python-app.zip\', \'w\', zipfile.ZIP_DEFLATED); z.write(\'app.py\'); z.close()"'

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
```
