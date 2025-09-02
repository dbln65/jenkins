pipeline {
    agent none
    stages {
        stage('Build & Test') {
            agent {
                docker {
                    image 'maven:3.9.11-eclipse-temurin-17'
                    args '-v $HOME/.m2:/root/.m2'  // Optional: persist Maven cache
                }
            }
            steps {
                // Checkout code from Git repository
                checkout scm

                // Build Maven project
                sh 'mvn clean install'

                // Run tests
                sh 'mvn test'

                // Publish test reports in Jenkins
                junit '**/target/surefire-reports/*.xml'
            }
        }
    }
}
