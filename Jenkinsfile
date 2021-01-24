// Declarative //
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
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
    git branch: 'main',
        url: 'https://github.com/ta2000riq/ng-hello.git'
    stage('NPM Install') {
          bat 'npm install'
    }
    stage('build') {
          bat 'npm run ng build --prod'
    }
    stage('make dir') {
          bat 'md %WORKSPACE%\dist\sourcemaps\'
    }
    stage('move source to dir') {
          bat 'move %WORKSPACE%\dist\ng-hello\*.map %WORKSPACE%\dist\sourcemaps\'
    }
	stage('zip dist files') {
          bat 'powershell Compress-Archive dist/ng-hello/ dist/ng-hello/publish.zip'
    }  
    stage('Build') {
        echo 'Building....'
    }
    stage('Test') {
        echo 'Building....'
    }
    stage('Deploy') {
        echo 'Deploying....'
    }
}
