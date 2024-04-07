pipeline {
  agent { label 'spc' }
  stages {
	stage('git') {
		  steps {
			git url: 'https://github.com/spring-projects/spring-petclinic.git', branch: 'main'
		  }
	}
	stage('build') {
	  steps {
		mail bcc: '', body: 'Build started', cc: '', from: '', replyTo: '', subject: 'Build started', to: 'all@learnigthoughts.io'
		sh 'mvn clean package'
		junit testResults: '**/surefire-reports/*.xml'
		archive '**/target/spring-petclinic-*.jar'
		mail bcc: '', body: 'Build completed', cc: '', from: '', replyTo: '', subject: 'Build completed', to: 'all@learnigthoughts.io'
	  } 
	}
	stage('tests'){
		steps {
			sh 'echo running selenium test'
			sh 'echo running api tests'
			sh 'echo running performance test'
		}
	}
	
  }
    
}
