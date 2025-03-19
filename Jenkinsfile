pipeline {
	agent any
	triggers {
		githubPush()
	}
	environment {
		DOTNET_ROOT = tool name: 'dotnet-sdk', type: 'com.microsoft.jenkins.dotnet.DotNetSDK'
		DEPLOY_PATH = '/usr/projects/dan'
	}
	stages {
		stage('Checkout') {
			steps {
		  		git branch: 'main', url: 'https://github.com/wei-dan/Dan.git'
	      		}
	  	}
		stage('Restore') {
	 		steps {
				sh '${DOTNET_ROOT}/dotnet restore'
			}
		}
	  	stage('Build') {
	      		steps {
		  		sh '${DOTNET_ROOT}/dotnet build --configuration Release'
	      		}
		}
		stage('Publish') {
			steps {
				sh '${DOTNET_ROOT}/dotnet publish --configuration Release --output ./publish'
			}
		}
		stage('Deploy') {
			steps {
			
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


