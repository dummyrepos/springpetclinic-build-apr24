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
		sh "mvn ${params.MAVEN_GOAL}"
		junit testResults: '**/surefire-reports/*.xml'
		archive '**/target/spring-petclinic-*.jar'
	  }
	}
	
  }
    
}
