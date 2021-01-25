// Declarative //
pipeline {
    agent any

    stages {
         stage('Checkout') {
          steps {
            script {
               // The below will clone your repo and will be checked out to master branch by default.
               git branch: 'main', url: 'https://github.com/ta2000riq/ng-hello.git'
               // Checkout to a specific branch in your repo.
               // sh "git checkout main"
              }
           }
        }
        stage('NPM Install') {
			steps {
              bat 'npm install'
			}
        }
        stage('build') {
			steps {
              bat 'npm run ng build --prod'
			}
        }
        stage('make dir') {
			steps {
              bat "md ${env.WORKSPACE}\\dist\\sourcemaps\\"
			}
        }
        stage('move source to dir') {
			steps {
              bat "move ${env.WORKSPACE}\\dist\\ng-hello\\*.map ${env.WORKSPACE}\\dist\\sourcemaps\\"
			}
        }
      stage('zip dist files') {
	  		steps {
              bat "powershell Compress-Archive ${env.WORKSPACE}\\dist\\ng-hello\\ ${env.WORKSPACE}\\dist\\ng-hello\\publish.zip"
			}
        }
        stage('Deploy End') {
            steps {
                echo 'Deploying....'
            }
        }

					  
    }
	post { 
        always { 
            cleanWs()
        }
    }
}
