pipeline {
    agent any
    tools {
        nodejs 'nodejs' 
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/virtualram-rgb/angular-realworld-example-app.git'
            }
        }
        stage ('Exec npm install') {
            steps {
                 sh 'npm install'
            }
        }
        stage('build'){
            steps{
                 sh 'npm run build'
            }
        }
        
        stage ('Exec npm publish') {
            steps {
                sh 'npm publish'
            }
        }
        stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "Jfrog_instance"
                )
            }
        }
    }
}
