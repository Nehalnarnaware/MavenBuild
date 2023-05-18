pipeline {
    agent any 
    environment{
	PATH = /opt/maven/bin:$PATH
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Nehalnarnaware/MavenBuild.git'
            }
        
	}
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
	}
	 stage('Deploy to Tomcat') {
            environment {
                TOMCAT_URL = 'http://18.237.6.225:8080/'  // Replace with your Tomcat server URL
                TOMCAT_USERNAME = 'tomcat'  // Replace with your Tomcat username
                TOMCAT_PASSWORD = credentials('Nehal@123')  // Use Jenkins credentials for password
            }
            steps {
                script {
                    sh "curl -T target/MavenBuild.war --user $TOMCAT_USERNAME:$TOMCAT_PASSWORD $TOMCAT_URL/manager/text/deploy?path=/MavenBuild"
          }
	}	 
    }	   
  }
}
