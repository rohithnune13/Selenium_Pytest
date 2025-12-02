pipeline {
    agent any

    stages {
        stage('Setup Python') {
            steps {
                bat """
                C:\\Users\\rohit\\AppData\\Local\\Programs\\Python\\Python314\\python.exe --version
                C:\\Users\\rohit\\AppData\\Local\\Programs\\Python\\Python314\\python.exe -m pip install --upgrade pip
                C:\\Users\\rohit\\AppData\\Local\\Programs\\Python\\Python314\\python.exe -m pip install -r requirements.txt
                """
            }
        }

        stage('Run PyTest Tests') {
            steps {
                bat """
                C:\\Users\\rohit\\AppData\\Local\\Programs\\Python\\Python314\\python.exe -m pytest --html=report.html --self-contained-html
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
