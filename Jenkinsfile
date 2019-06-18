pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'java -jar target/${NAME}-${VERSION}.jar'
                sh 'set +x'
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}
