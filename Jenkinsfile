pipeline {
	agent {
		docker {
			image 'node:lts-bullseye-slim'
			args '-p 3000:3000'
		}
	}
	stages {
		stage('Build') {
			steps {
				echo 'Here build step!'
				sh 'npm install'
			}
		}
		stage('Test') {
			steps {
				echo 'Here test step!'
				sh './jenkins/scripts/test.sh'
			}
		}
		stage('Deploy') {
			steps {
				sh './jenkins/scripts/deliver.sh'
				input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
				sh './jenkins/scripts/kill.sh'
			}
		}
	}
}

