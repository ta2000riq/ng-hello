// Declarative //
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Start building..'
            }
        }
        
        def workspace = WORKSPACE
        git branch: 'main',
            url: 'https://github.com/ta2000riq/ng-hello.git'
        stage('NPM Install') {
              bat 'npm install'
        }
             stage('build') {
              bat 'npm run ng build --prod'
        }
        stage('make dir') {
              bat 'md ${pwd()}\\dist\\sourcemaps\\'
        }
        stage('move source to dir') {
              bat 'move ${pwd()}\\dist\\ng-hello\\*.map ${pwd()}\\dist\\sourcemaps\\'
        }
      stage('zip dist files') {
              bat 'powershell Compress-Archive ${pwd()}\\dist\\ng-hello\\ ${pwd()}\\dist\\ng-hello\\publish.zip'
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
// Script //
node {
    stage('Deploy') {
        echo 'Node Deploying....'
    }
}
