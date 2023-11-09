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
		deploy adapters: [tomcat9(credentialsId: 'fdf772ec-e644-4752-998b-806dab8239d0', path: '', url: 'http://15.207.112.234:8080/')], contextPath: null, war: '**/*.war'
	}

}
