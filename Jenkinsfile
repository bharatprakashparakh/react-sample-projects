pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS 21.1'  // Make sure this version is correctly installed in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                cleanWs()  // Optional: clean workspace before checkout
                echo "Checking out..."
                checkout scm  // Checkout the code from the repository
            }
        }
        
        stage('Install Dependencies') {
            steps {
                script {
                    echo "Installing dependencies..."
                    sh 'npm install'  // Install dependencies
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building the React app..."
                    sh 'npm run build'  // Build the React app
                }
            }
        }
    }
}
