pipeline {
    agent any

    stages {  
        stage ("build") {
            tools {
               jdk-1.8.0_181
            }
            steps {
                sh 'java Hello.jar'
            }
        }          
   }
}
