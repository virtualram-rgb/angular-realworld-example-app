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
        stage ('Artifactory configuration') {
            steps {
                rtServer (
                    id: "ARTIFACTORY_SERVER",
                    url: "https://virtualhost.jfrog.io/",
                    credentialsId: "jfrog_creds"
                )
                rtNpmDeployer (
                    id: "NPM_DEPLOYER",
                    serverId: "Jfrog_instance",
                    repo: "npmproject1-npm"
                )
            }
        }
        stage ('Exec npm install') {
            steps {
                rtNpmInstall (
                    tool: "nodejs", // Tool name from Jenkins configuration
                    path: "package.json"
                )
            }
        }
        stage('build'){
            steps{
                 sh 'npm run build'
            }
        }
        
        stage ('Exec npm publish') {
            steps {
                rtNpmPublish (
                    tool: "nodejs", // Tool name from Jenkins configuration
                    path: "package.json",
                    deployerId: "NPM_DEPLOYER"
                )
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
