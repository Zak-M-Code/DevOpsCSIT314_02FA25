pipeline {
	agent any
	stages {
		stage('Checkout') {
			setps {
				git url: 'https://github.com/Zak-M-Code/DevOpsCSIT314_02FA25.git',
					branch: '*/main',
					credentialsId: 'Github-Access-Token-Midterm'
			}
		}
		stage('Build') { steps { sh './mvnw clean package' } }
		stage('Archive') {steps { archiveArtifacts artifiacts: 'target/*.jar', fingerprint: true } }
	}
}		
