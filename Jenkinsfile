pipeline{
  agent any
  stages{
       stage('Clean Workspace'){
      steps {
        cleanWs()
      }
    }
    
    stage('Checkout'){
      steps {
        checkout([$class: 'GitSCM', 
        branches: [[name: '*/main']], 
        doGenerateSubmoduleConfigurations: false, 
        extensions: [], 
        submoduleCfg: [], 
        userRemoteConfigs: [[url: 'https://github.com/ta2000riq/ng-hello.git']]])

      }
    }
    stage ('install modules'){
      steps{
        sh '''
          npm install
        '''
      }
    }
    stage ('code quality'){
      steps{
        sh '$(npm bin)/ng lint'
      }
    }
    stage ('build') {
      steps{
        sh '$(npm bin)/ng build --prod'
      }
    }
  }
}
