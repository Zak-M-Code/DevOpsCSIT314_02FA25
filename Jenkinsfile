pipeline {
	agent any
	stages {
		stage('Checkout') {
			steps {
				checkout([$class: 'GitSCM',
					branches: [[name: '*/main']],
					userRemoteConfigs: [[url: 'https://github.com/Zak-M-Code/DevOpsCSIT314_02FA25.git', credentialsId: 'GitHub-Access-Token-Midterm']]])
			}
		}
		stage('Prepare') {
			steps {
				sh 'ls -la'
			}
		}
		stage('Build') {
			 steps {
				dir('complete') {
					sh 'test -f ./mvnw && chmod +x ./mvnw || true'
					sh '''
						if [ -x ./mvnw ]; then
							./mvnw clean package
						elif command -v mvn >/dev/null 2>&1; then
							mvn clean package
						elif command -v gradle >/dev/null 2>&1 || [ -f gradlew ]; then
							./gradlew build
						else
							echo "not found" >&2
							exit 1
						fi
					'''
				}
			}
		}
 		stage('Archive') {
			steps {
				archiveArtifacts artifacts: 'complete/target/*.jar',complete/build/libs/*.jar', fingerprint: true
			 }
		}
	}
	post {
		always {
			sh 'ls -la complete || true'
		}
	}
}
