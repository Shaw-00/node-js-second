pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-hub-task')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t rishaw00/node-js-sample:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push rishaw00/node-js-sample:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
