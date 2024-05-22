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
                
                deploy adapters: [tomcat9(credentialsId: 'Tomcat-test-Server', path: '', url: 'http://13.201.61.115:8080/')], contextPath: '/app', war: '**/*.war'
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
