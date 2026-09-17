pipeline {
    agent any

    parameters {
        booleanParam(name: 'RUN_EXTRA_CHECK', defaultValue: true, description: 'Run the extra check stag4')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Sid-DeadSkull11/jenkins-lab-4.git'
            }
        }

        stage('Build') {
            steps {
                bat '"C:\\Users\\siddh\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe" -m py_compile app.py'
                echo 'Build successful: app.py compiled with no syntax errors'
            }
        }

        stage('Extra Check') {
            when {
                expression { params.RUN_EXTRA_CHECK == true }
            }

            steps {
                echo 'Running extra check: verifying greet() output format...'
                bat '"C:\\Users\\siddh\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe" -c "from app import greet; print(greet(\'Student\'))"'
            }
        }
    }
}