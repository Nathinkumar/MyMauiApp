pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Nathinkumar/MyMauiApp.git'
            }
        }
         stage('Install Workloads') {
            steps {
                bat 'dotnet workload install maui'
            }
        }
          stage('Update Workloads') {
            steps {
                bat 'dotnet workload update maui'
            }
        }
        stage('Restore') {
            steps {
                bat 'dotnet restore MyApp.sln'
            }
        }

        stage('Build Android') {
            steps {
                bat 'dotnet build MyApp/MyApp.csproj -c Release -f net8.0-android'
            }
        }

        stage('Publish APK') {
    steps {
        bat 'dotnet publish MyApp/MyApp.csproj -c Release -f net8.0-android -o .\\output /p:AndroidPackageFormat=apk'
    }
}
    }
}
