pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/virtualram-rgb/js-e2e-express-server.git'
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
