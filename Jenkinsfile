pipeline {
    agent any

    tools {
        jdk 'JDK21'       // Your JDK name in Jenkins
        maven 'maven3.9.11'    // Your Maven name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/IshuM210/java-app.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Run Java Program') {
            steps {
                // Run your Java main class and print output to Jenkins console
                bat 'java -cp target\\MyJavaApp-1.0-SNAPSHOT.jar com.example.LargestNumber'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Build completed successfully!'
        }
        failure {
            echo '❌ Build failed. Check console output!'
        }
    }
}
