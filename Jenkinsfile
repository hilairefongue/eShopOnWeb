pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet Unit tests/testsunitaires'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/integrationstests'
          }
        }

        stage('Fonctionnels') {
          steps {
            sh 'dotnet test tests/Fonctionnaltests'
          }
        }

      }
    }

    stage('Deploiement') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}