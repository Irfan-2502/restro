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
		deploy adapters: [tomcat9(credentialsId: 'dcddd3c2-a013-4da8-9f28-fc6d928f10db', path: '', url: 'http://52.66.242.19:8080/')], contextPath: null, war: '**/*.war'
	}

}
