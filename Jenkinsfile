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
                
                
                
                sh 'visudo mvn jar:jar install:install help:evaluate -Dexpression=project.name'
                sh 'visudo NAME=`mvn help:evaluate -Dexpression=project.name | grep "^[^\[]"`'
                sh 'visudo VERSION=`mvn help:evaluate -Dexpression=project.version | grep "^[^\[]"`'
                sh 'visudo java -jar target/${NAME}-${VERSION}.jar'
                
            }
        }
    }
}

