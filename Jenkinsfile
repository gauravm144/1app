pipeline {
    agent any

    tools {
        // Specify the JDK and Maven tools configured in Jenkins
        jdk 'JDK_17' // Name of your JDK configuration
        maven 'Maven_3.9.10' // Name of your Maven configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/gauravm144/1app.git' // Replace with your repo and branch
            }
        }
        stage('Build') {
            steps {
                // Use bat for Windows commands
                bat 'mvn clean package'
            }
        }
        stage('Run Application') {
            steps {
                // This will run the application and block the pipeline until it's stopped.
                // For actual deployment, consider running as a background process or deploying to a server.
                bat 'java -jar target\\your-app-name.jar'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished!'
        }
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}