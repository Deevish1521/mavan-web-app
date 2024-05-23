pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    stages{
        stage("App-Test"){
            steps{
                // maven test
                sh 'mvn test'
            }
            
        }
        stage("App-Build"){
            steps{
                // maven Package
                sh 'mvn clean package'
            }
            
        }
        stage("app-deploye-test-env"){
            steps{
                // copy war file
                sshagent(['deploy_user']) {
                sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/test/target/maven-web-app.war ubuntu@13.233.133.112:/var/lib/tomcat10/webapps/'
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
