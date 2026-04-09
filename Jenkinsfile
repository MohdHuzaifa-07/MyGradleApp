pipeline {
    agent any

    tools {
        jdk 'JDK17'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/MohdHuzaifa-07/MyGradleApp.git'
            }
        }

        stage('Build') {
            steps {
                // Fix Gradle cache issue (Java 21 vs 17 conflict)
                sh 'rm -rf ~/.gradle/caches/'
                
                sh 'chmod +x gradlew'
                sh './gradlew build --no-daemon'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test --no-daemon'
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
