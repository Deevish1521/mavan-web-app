pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    stages{
        stage("Test-step"){
            steps{
                sh "mvn test"
            }
            
        }
        stage("Build-step"){
            steps{
                sh "mvn package"
            }
            
        }
        stage("Deploye-Test-Env"){
            steps{
                
                sshagent(['Tomcat-test-Server_SSH']) {
                sh 'cp /var/lib/jenkins/workspace/maven-web-app-pipeline/target/maven-web-app.war /var/lib/tomcat10/webapps/app.war'
    
            }
            }
            
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
