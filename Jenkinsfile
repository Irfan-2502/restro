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
		deploy adapters: [tomcat9(credentialsId: '7fb11f96-ed2d-43a1-9c17-45020497c9fe', path: '', url: 'http://65.0.72.129:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
	}

}
