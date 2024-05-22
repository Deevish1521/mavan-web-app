pipeline{
    agent any
    tools {
        maven "Maven"
    }
    stages{
        stage("Test-app"){
            steps{
                
                sh "mvn test"
            }
           
        }
        stage("Build-app"){
            steps{
                
                sh "mvn package"
            }
           
        }
         stage("Deploye-Test-Env"){
            steps{
                
                deploy adapters: [tomcat9(credentialsId: '6351f3a2-f402-4cc1-93a0-27d298e86e9a', path: '', url: 'http://13.232.1.230:8080/')], contextPath: '/app', war: '**/*.war'
            }
           
        }
         stage("Deploye-Prod-Live-Env"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '6351f3a2-f402-4cc1-93a0-27d298e86e9a', path: '', url: 'http://13.233.113.74:8080/')], contextPath: '/app', war: '**/*.war'
               
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
