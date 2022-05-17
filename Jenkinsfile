pipeline{
    agent any

    tools {
         maven 'maven3'
        
    }

    stages{
        stage('checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/Arungangoni/hello-world.git']]])
            }
        }
        stage('build'){
            steps{
               sh 'mvn install'
            }
        }
        stage(deploy){
            steps{
                sshagent(['deploy_user']){
                    sh "scp -o StrictHostKeyChecking=no /target/webapp.war ec2-user@3.88.129.66:/opt/tomcat/apache-tomcat-9.0.48/webapps"
                }
      }
        
    }
    }
}
