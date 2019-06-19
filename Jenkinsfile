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
                sh 'mvn clean install'
                sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
                 
            }
        }
    }
}
