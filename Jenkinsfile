pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git url: 'git@github.com:mhost52/netcorejenkinstest.git', credentialsId: 'github-ssh-key'
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore Testing.sln'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build Testing.sln --configuration Release'
            }
        }

        stage('Publish') {
            steps {
                bat 'dotnet publish SimpleApp/SimpleApp.csproj -c Release -o C:\\inetpub\\wwwroot\\simpleapp'
            }
        }
    }

    post {
        success {
            echo '✅ Deploy sukses ke IIS!'
        }
        failure {
            echo '❌ Build atau deploy gagal.'
        }
    }
}