node {
	stage('prepare') {
		git branch: 'main', poll: false, url: 'https://github.com/Irfan-2502/restro.git'
	}
	
	stage('build') {
		def mvnHome = tool 'MAVEN'
		withEnv(["MVN_HOME=$mvnHome"]){
			sh '"$MVN_HOME/bin/mvn" clean compile package'
		}
	}
	
	stage('deploy') {
		deploy adapters: [tomcat9(credentialsId: '9de4d29d-dd79-4aa7-85bb-629247c18db8', path: '', url: 'http://52.66.242.19:8080/')], contextPath: null, war: '**/*.war'
	}

}
