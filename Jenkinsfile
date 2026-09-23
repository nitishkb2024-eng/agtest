pipeline {
    agent any

    environment {
        APP_NAME    = 'MyPythonApp'
        APP_VERSION = '1.2.0'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out source code for ${env.APP_NAME}..."
                // Simulating repository checkout
                checkout scm: [
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/nitishkb2024-eng/agtest.git']]
                ]
            }
        }

        stage('Build') {
            steps {
                echo "Performing compile check on app.py..."
                // Changed from 'sh' to 'bat' for Windows compatibility
                bat 'python -m py_compile app.py'
            }
        }

        stage('Deploy') {
            steps {
                input message: "Approve deployment of ${env.APP_NAME} version ${env.APP_VERSION}?", ok: "Release"
                
                echo "Deploying ${env.APP_NAME} v${env.APP_VERSION}..."
                // Changed from 'sh' to 'bat' for Windows compatibility
                bat 'python app.py'
            }
        }
    }
}
