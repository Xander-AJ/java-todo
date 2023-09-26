pipeline {
    agent any
    environment {
        GITHUB_REPO_URL = 'https://github.com/Xander-AJ/java-todo'
        GITHUB_CREDENTIALS_ID = 'Xander-AJ'
    }
    stages {
        stage('Clone repository') {
            steps {
                // Clone the GitHub repository using the generic 'git' step
                git credentialsId: GITHUB_CREDENTIALS_ID, url: GITHUB_REPO_URL
            }
        }
        stage('Install Gradle') {
            steps {
                // Install Gradle tool
                tool name: 'Gradle 8.3', type: 'Gradle'
            }
        }
        stage('Tests') {
            steps {
                sh 'gradle test'
            }
        }
        stage('Build project') {
            steps {
                sh 'gradle build'
            }
        }
    }
}
