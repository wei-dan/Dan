pipeline {
	agent any
	stages {
		stage('Checkout') {
			steps {
		  		git branch: 'main', url: 'https://github.com/wei-dan/Dan.git'
	      		}
	  	}
		stage('Restore') {
	 		steps {
				sh 'dotnet restore'
			}
		}
	  	stage('Build') {
	      		steps {
		  		sh 'dotnet build --configuration Release'
	      		}
		}
		stage('Publish') {
			steps {
				sh 'dotnet publish --configuration Release --output /usr/projects/dan/publish'
			}
		}
		stage('Deploy') {
			steps {
				sh "systemctl restart dan"
			}
		}
	}
	post {
		success {
			echo "deploy success"
		}
		failure {
			echo "deploy failed"
		}
	}
}
