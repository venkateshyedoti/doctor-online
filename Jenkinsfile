pipeline {
    agent any
    parameters {
  choice choices: ['dev', 'test', 'prod'], description: 'choose to environment to deploy', name: 'envName'
}

    stages {
       
        stage("maven builds") {
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
            steps {
               echo "deploy to test"
                }
            }
        stage("Deploy to prod") {
            steps {
               echo "deploy to prod"
                }
            }
        }
    }
