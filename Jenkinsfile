pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/virtualram-rgb/angular-realworld-example-app.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
                }
            }
        stage('build'){
            steps{
                 sh 'npm run build'
            }
        }
        
        stage('Deploy') {
            steps {
             sh 'npm publish'
            }
        }
    }
}
