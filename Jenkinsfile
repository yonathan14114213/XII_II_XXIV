pipeline {
    agent { 
        docker { 
            image 'node:14' 
            args '-u root' // This is added to run Docker container with root user privileges
        } 
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from version control
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install project dependencies using npm or yarn
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                // Build the project (e.g., transpile TypeScript, bundle assets, etc.)
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                // Run tests (e.g., unit tests, integration tests, etc.)
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy the application (e.g., to a server, cloud provider, etc.)
                // This step will depend on your deployment strategy
                // Example: sh 'npm run deploy'
            }
        }
    }
    post {
        always {
            // Clean up steps, e.g., delete temporary files, stop containers, etc.
            cleanWs()
        }
        success {
            // Actions to perform if the pipeline is successful
            echo 'Pipeline succeeded! Application is ready for deployment.'
        }
        failure {
            // Actions to perform if the pipeline fails
            echo 'Pipeline failed. Review the logs for errors.'
        }
    }
}
