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
                sh 'mvn install:install-file "-Dfile=cobra.jar" "-DgroupId=com.cobra" "-DartifactId=cobra" "-Dversion=0.98.4" "-Dpackaging=jar" "-DgeneratePom=true"'
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}
