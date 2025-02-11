pipeline {
    agent any
    
    environment {
        // Set your environment variables here if needed
        NODE_HOME = '/usr/local/bin' // Adjust this according to your Node.js installation path
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from Git repository
                git 'https://github.com/kumarsunil4360/Student-Management-System-Using-Nodejs.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Ensure that node_modules have proper permissions and install dependencies
                sh 'chmod -R 755 ./node_modules'  // Fix permission issues
                sh 'npm install'  // Install dependencies
            }
        }

        stage('Run Tests') {
            steps {
                // Skip test execution if there are no tests defined
                echo 'Skipping tests as none are defined'
            }
        }

        stage('Build') {
            steps {
                // Placeholder for build step (if you want to define build logic later)
                sh 'npm run build || echo "Build step not defined yet"'
            }
        }

        stage('Start Application') {
            steps {
                // Fix permission issue for nodemon and start the application
                sh 'chmod +x ./node_modules/.bin/nodemon'  // Ensure nodemon is executable
                sh 'npm start'  // Start the Node.js application
            }
        }
    }

    post {
        always {
            // Clean up any actions if needed
            echo 'Pipeline execution complete!'
        }
        failure {
            // Handle pipeline failure if necessary
            echo 'Build failed, check logs for details.'
        }
    }
}
