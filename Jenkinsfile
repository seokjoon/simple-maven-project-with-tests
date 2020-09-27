node('master') {

	stage('Preparation') {
    		git 'https://github.com/seokjoon/simple-maven-project-with-tests.git'
	}
	stage('Build') {
    		withMaven(maven: 'M3') {
			if(isUnix()) {
				sh 'mvn -Dmaven.test.failure.ignore clean package'
			} else {
				bat 'mvn -Dmaven.test.failure.ignore clean package'
			}
		}
	}
	stage('Results') {
		unit '**/target/surefire-report/TEST-*.xml'
		archive 'target/*.jar'
	}
}
