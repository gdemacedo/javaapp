pipeline {
    agent any
    
    tools {
        maven 'Mvn'
        jdk 'JDK9'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
