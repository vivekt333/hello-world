pipeline {
    agent any
  environment {
      PATH = "/opt/apache-maven-3.9.1/bin:$PATH"
  }
    stages {
        stage('Clone code') {
            steps {
                git credentialsId : 'git cred', url: 'https://github.com/thakur-vvk/hello-world'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('SSH') {
            sshagent(['deploy_user']) {
                sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@13.229.183.126:/opt/apache-tomeat-8.5.5S/webapps"
                
            } 
        }
    }
}
