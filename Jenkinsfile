pipeline {
    agent any

    tools {
        maven "default"
    }

    stages {
        stage('Build') {
            agent any
		
	    steps
	    {
		echo "Build stage"
               
                git branch: 'master', url: 'https://github.com/minutuscomputing/sample-java-application.git', credentialsId:'github_meghana'

                sh "mvn -Dmaven.test.failure.ignore=true clean test package install"
             }
        }
         stage('deploy') {
          agent any
	    steps 	   
	    {
	        sshagent(['tomcat']) {
	          sh "scp -o StrictHostKeyChecking=no target/studentapp-2.5-SNAPSHOT.war ec2-user@18.222.220.43:/opt/tomcat/webapps"
	        }
	    }
         }
    }
}