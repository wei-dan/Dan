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
        sh 'dotnet restore ./src/Dan.Web/Dan.Web.csproj'
      }
    }
    stage('Build') {
      steps {
          sh 'dotnet build ./src/Dan.Web/Dan.Web.csproj --configuration Release'
            }
    }
    stage('Publish') {
      steps {
        sh 'dotnet publish ./src/Dan.Web/Dan.Web.csproj --configuration Release --output /usr/projects/dan/publish'
      }
    }
    stage('Deploy') {
      steps {
        sh "sudo systemctl restart dan"
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

