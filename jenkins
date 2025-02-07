pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'npm install' // If using Node.js, for C# use 'dotnet build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test' // For C#, use 'dotnet test'
            }
        }

        stage('Code Quality Analysis') {
            steps {
                echo 'Running SonarQube analysis...'
                sh 'sonar-scanner' // Ensure SonarQube is configured in Jenkins
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to staging...'
                sh 'docker-compose up -d' // Adjust based on your deployment method
            }
        }

        stage('Release') {
            steps {
                echo 'Promoting to production...'
                sh 'aws deploy push' // Example for AWS
            }
        }

        stage('Monitoring & Alerting') {
            steps {
                echo 'Setting up monitoring...'
                sh 'newrelic-admin run-program npm start' // Example using New Relic
            }
        }
    }
}
