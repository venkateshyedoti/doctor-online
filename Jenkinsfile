pipeline {
    agent any
    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', credentialsId: 'git-creds', url: 'https://github.com/venkateshyedoti/doctor-online'
            }
        }
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
