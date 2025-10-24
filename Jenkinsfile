pipeline {
	agent any
	stages {
		stage('Checkout') {
			steps {
				checkout([$class: 'GitSCM',
					branches: [[name: '*/main']],
					userRemoteConfigs: [[url: 'https://github.com/Zak-M-Code/DevOpsCSIT314_02FA25.git']]]
				)
			}
		}
		stage('Prepare') {
			 steps {
				sh 'ls -la'
				sh 'test -f ./mvnw && chmod +x ./mvnw || true'
			}
		}
		stage('Build') {
			steps {
				sh './mvnw clean package'
			}
		}
 		stage('Archive') {
			steps {
				archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
			 }
		}
	}
	post {
		always {
			sh 'ls -la target || true'
		}
	}
}
		
