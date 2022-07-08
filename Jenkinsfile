pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Docker')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t nodejs .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Tag') {
		      
			steps {
				sh 'docker tag nodejs ypratik127/nodejs:latest'
			        echo "Tagging done"	
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
