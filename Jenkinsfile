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
		deploy adapters: [tomcat9(credentialsId: '948ec2c3-db4f-4966-a3aa-b81d2ac89d82', path: '', url: 'http://52.40.25.7:8080/')], contextPath: null, war: '**/*.war'

}

