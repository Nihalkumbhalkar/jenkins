pipeline {
  agent any
  
    stages {
        stage('Checkout') {
        steps {
            git branch: 'main', url: 'https://github.com/Nihalkumbhalkar/angular_project.git'
        }
        } 
        stage('Build') {
        steps {
            bat 'npm install'
            bat 'npm run build --prod'
        }
        }
        stage('Host on Localhost') {
            steps {
                bat 'npm install -g http-server'
                bat 'http-server dist/first-app -p 4500 --open'
                echo "Application is running on localhost:4500"
            }
        }
        stage('Open in Browser') {
        steps {
            script {
            def hostIp = bat(returnStdout: true, script: 'echo %COMPUTERNAME%').trim()
            echo "Application hosted at: http://${hostIp}:4500"
            }
        }
        }
    }
}