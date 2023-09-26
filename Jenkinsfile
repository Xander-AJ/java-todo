pipeline {
    agent any
    tools {
        // Install or configure the Gradle tool using the 'Tool Configuration' in Jenkins.
        gradle "Gradle 8.3"
    }
    environment {
        GITHUB_REPO_URL = 'https://github.com/Xander-AJ/java-todo'
        GITHUB_CREDENTIALS_ID = 'Xander-AJ'
    }
    stages {
        stage('Install Gradle') {
            steps {
                // This stage will install or configure the Gradle tool.
                // You can specify the desired Gradle version, e.g., "Gradle 8.3".
                // The tool name should match the name defined in the Jenkins 'Tool Configuration.'
                script {
                    def gradleHome = tool 'Gradle 8.3'
                    env.PATH = "${gradleHome}/bin:${env.PATH}"
                }
            }
        }
        stage('Clone repository') {
            steps {
                git credentialsId: GITHUB_CREDENTIALS_ID, url: GITHUB_REPO_URL
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
