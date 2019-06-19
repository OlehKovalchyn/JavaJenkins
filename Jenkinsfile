pipeline {
    agent any 
  tools {
        maven 'Maven 3.3.9'
        jdk 'JDK8'
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
               
                sh 'visudo ./jenkins/scripts/deliver.sh'
                
            }
        }
    }
}

