pipeline{
  agent { label 'nodejs8' }
  stages{
    stage ('checkout'){
      steps{
        checkout scm
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
