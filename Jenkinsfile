pipeline {
    agent any

    stages {
       
        
        stage('Build') {
            steps {
                sh """
                
                mvn clean
                mvn compile
                
                """
                
               
            }
        }
        
        stage('Test') {
            steps {
               
               sh "mvn test"
            }
            
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Package') {
            steps {
               
               sh "mvn -X package"
            }
            
            post {
                always {
                    archiveArtifacts artifacts: 'target/*.jar'
                }
            }
        }
    }
}
