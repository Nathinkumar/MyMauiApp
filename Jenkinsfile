pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Nathinkumar/MyMauiApp.git'
            }
        }

        stage('Restore') {
            steps {
                sh 'dotnet restore MyApp.sln'
            }
        }

        stage('Build Android') {
            steps {
                sh 'dotnet build MyApp/MyApp.csproj -c Release -f net8.0-android'
            }
        }

        stage('Publish APK') {
            steps {
                sh 'dotnet publish MyApp/MyApp.csproj -c Release -f net8.0-android -o ./output'
            }
        }
    }
}
