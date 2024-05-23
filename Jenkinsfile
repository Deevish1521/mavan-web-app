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
