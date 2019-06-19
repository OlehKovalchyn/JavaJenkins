pipeline {
    agent {
  tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
        
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
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh 'root ALL=(ALL) ALL'
                sh 'set +x deliver.sh'
                sh './deliver.sh'
            }
        }
    }
}

