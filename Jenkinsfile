// pipeline {
//     agent any
    
//     tools {
//         nodejs 'NodeJS 21.1'  // Make sure this version is correctly installed in Jenkins
//     }

//     stages {
//         stage('Checkout') {
//             steps {
//                 cleanWs()  // Optional: clean workspace before checkout
//                 echo "Checking out..."
//                 checkout scm  // Checkout the code from the repository
//             }
//         }
        
//         stage('Install Dependencies') {
//             steps {
//                 script {
//                     echo "Installing dependencies..."
//                     sh 'npm install'  // Install dependencies
//                 }
//             }
//         }

//         stage('Build') {
//             steps {
//                 // Build Next.js project
//                 nodejs(nodeJSInstallationName: 'NodeJS 21.1') {
//                     sh 'npm run build'
//                 }
//             }
//         }
//     }
// }


//noinspection GroovyAssignabilityCheck
pipeline {
//     parameters {
//         choice(name: 'SCOPE', description: 'Update Scope', choices: ['patch','minor','major'] )
//         string(name: 'VERSION', description: 'Version', defaultValue: '' )
//     }

    options {
        buildDiscarder(logRotator(numToKeepStr: "20"))
    }

    agent any

    triggers {
        pollSCM('H/5 * * * *') // Polling every 5 minutes
    }

    stages {
        stage('Install Dependencies') {
            steps {
                // Install Node.js and dependencies
                nodejs(nodeJSInstallationName: 'NodeJS 21.1') {
                    sh 'ldd --version'
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                // Build Next.js project
                nodejs(nodeJSInstallationName: 'NodeJS 21.1') {
                    sh 'npm run build'
                }
            }
        }
    }

    post {
        success {
            // Notify on successful build
            echo 'Build successful!'
        }
        failure {
            // Notify on build failure
            echo 'Build failed!'
        }
    }
}
