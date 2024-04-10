pipeline {
  agent { label 'spc' }
  parameters {
	choice(name: 'MAVEN_GOAL', choices: ['package', 'clean package'], description: 'This is maven goal')
  }
  stages {
	stage('git') {
		  steps {
			git url: 'https://github.com/spring-projects/spring-petclinic.git', branch: 'main'
		  }
	}
	stage('build') {
	  steps {
		mail bcc: '', body: 'Build started', cc: '', from: '', replyTo: '', subject: 'Build started', to: 'all@learnigthoughts.io'
		sh 'mvn ${params.MAVEN_GOAL}'
		junit testResults: '**/surefire-reports/*.xml'
		archive '**/target/spring-petclinic-*.jar'
		mail bcc: '', body: 'Build completed', cc: '', from: '', replyTo: '', subject: 'Build completed', to: 'all@learnigthoughts.io'
	  } 
	}
	
  }
    
}
