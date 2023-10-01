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
        stage("Dev Deploy") {
            steps {
                sshagent(['tomcat-dev']) {
                  //copy war file to tomcat
                  sh "scp -o StrictHostKeyChecking=no target/doctor-online.war ec2-user@172.31.84.224:/opt/tomcat9/webapps"
                 //stop tomcat
                 sh "ssh ec2-user@172.31.84.224 /opt/tomcat9/bin/shutdown.sh"
                 //start tomcat
                 sh "ssh ec2-user@172.31.84.224 /opt/tomcat9/bin/startup.sh"
                }
            }
        }
    }
}
