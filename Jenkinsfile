pipeline {
    agent any

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
                sh "curl --upload-file target/myapp.war --user $TOMCAT_USERNAME:$TOMCAT_PASSWORD $TOMCAT_URL/manager/
	 }
	}	 
    }	   
}	
