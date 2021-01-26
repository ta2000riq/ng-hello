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
              bat '${env.WORKSPACE}\\node_modules\\@angular\\cli\\bin\\ng build --prod --base-href=/tdc-ui/ --optimization=true'
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
        steps{          	  		
          
			
				    bat "\"C:\\Program Files\\Java\\jdk1.8.0_181\\bin\\jar\" -cfM ${env.WORKSPACE}\\dist\\ng-hello\\ng-hello1.zip -C ${env.WORKSPACE}\\dist\\ng-hello\\ ."
            
        }
   }
      
    	   stage("archive_build") {
            steps {
                dir("${env.WORKSPACE}\\dist\\ng-hello") {
                  archiveArtifacts "ng-hello1.zip"
                }
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
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        
    }

}
