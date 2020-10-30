pipeline {
    agent any
    
    tools {
        maven 'Mvn'
        jdk 'JDK9'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Running maven command'
                sh 'mvn -B -DskipTests clean package'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                    step([
                        $class           : 'JacocoPublisher',
                        execPattern      : '**/**.exec',
                        classPattern     : '**/classes',
                        sourcePattern    : '**/src/main/java',
                        exclusionPattern : '**/*Test.class'
                    ])
                }
            }
        }
    }
}
