pipeline {
    agent any
	
	  tools
    {
       maven "Maven"
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/devops4solutions/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

         stage("maven build"){
               pipeline{
                //plugin deply on container
                deploy adapters: [tomcat9(credentialsId: '3c2d8288-2802-49e4-8838-668f97bc15f2', path: '', url: 'http://192.168.0.108:8080')], contextPath: '/app', war: '**/*.war'
                echo "Deploy Build"
            }
        }
    }
