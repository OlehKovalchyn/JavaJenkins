pipeline {
    agent {
        docker {
            image 'sudo maven:3-alpine'
            args  'sudo -v /root/.m2:/root/.m2'
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

