pipeline {
    agent any
    parameters {
  choice choices: ['dev', 'test', 'prod'], description: 'choose to environment to deploy', name: 'envName'
}

    stages {
       
        stage("maven builds") { 
            when{
                expression {params.envName == "dev"}
            }
            
            steps {
                sh "mvn clean package"
                
            }
        }
        stage("Deploy dev") {
            when{
                expression {params.envName == "dev"}
            }
            steps {
               echo params.envName
               echo "deploy to dev"
                }
            }
        stage("deploy to test") {
             when{
                expression {params.envName == "test"}
            }
            steps {
               echo "deploy to test"
                }
            }
        stage("Deploy to prod") {
             when{
                expression {params.envName == "prod"}
            }
            steps {
               echo "deploy to prod"
                }
            }
        }
    }
