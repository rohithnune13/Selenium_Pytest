pipeline {
    agent any

    stages {
        stage('Setup Python') {
            steps {
                bat """
                python --version
                python -m pip install --upgrade pip
                pip install -r requirements.txt
                """
            }
        }

        stage('Run PyTest Tests') {
            steps {
                bat """
                pytest --html=report.html --self-contained-html
                """
            }
        }

        stage('Archive HTML Report') {
            steps {
                archiveArtifacts artifacts: 'report.html', fingerprint: true
            }
        }
    }
}
