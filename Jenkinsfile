pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub') # the ID of the docker credentials that you created in step 5
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t bharathirajatut/nodeapp:latest .' # your docker hub name/repo
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push bharathirajatut/nodeapp:latest' # your dockerhub name/repo
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}

