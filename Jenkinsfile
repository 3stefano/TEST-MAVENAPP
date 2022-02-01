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
         stage('RUN APP') {
            steps {
                echo "RUNNING THE APP MY BOIIIIIIIIII"
                sh """
                
                export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -jar -DServer.port=8001 target/spring-petclinic-2.3.1.BUILD-SNAPSHOT.jar	&
                
                """
                
               
            }
        }
    }
}
