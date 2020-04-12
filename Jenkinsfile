pipeline {
	agent any
	stages {
		stage('Checkout') {
			steps {
					git 'https://github.com/edureka-git/DevOpsClassCodes.git'
				}
		}
	
		stage('Build') {
			steps {
					dir('') {
					sh '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/Maven3.6.3/bin/mvn -B -V -U -e clean package'
				}
			}
		}
		
		stage('Deployment') {
			steps {
					script {
					echo "Deployment"
					sh 'sudo cp /var/lib/jenkins/workspace/DevPipeline/target/addressbook.war /usr/share/tomcat/webapps/'
				}
			}
		}

		stage('Email') {
			steps {
					emailext attachLog: true, body: 'The status of the build can be obtained from the build log attached', subject: 'STATUS: $PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!', to: 'iamdevopsarch@gmail.com'
				}
		}

	
	}
	
}
