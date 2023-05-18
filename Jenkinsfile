

	
node('master'){	
	stage('Code Checkout'){
		checkout scm
		
	}
	stage('Build Automation'){
		sh "mvn clean install -Dmaven.test.skip=true"
	}
	
	stage('Test Cases Execution'){
		sh "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent -Pcoverage-per-test"
	}
	stage('Archive Artifacts'){
		archiveArtifacts artifacts= 'target/*.war'
	}
	
	stage('Code Deployment'){
		deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://18.237.6.225:8080/')], contextPath: 'counterwebapp', onFailure: false, war: 'target/*.war'
	}
}
