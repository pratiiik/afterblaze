pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Docker')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t ypratik127/nodejs:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push ypratik127/nodejs:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}