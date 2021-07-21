pipeline {
  agent any
  stages {
    stage('Audit Tool') {
      steps {
        echo "Audit all tools versions" 
        sh '''
            git --version
            ansible --version
            node --version
            npm --version
         '''
      }
    }
    stage('Get Source') {
      steps {
        echo "Get Source Code"
        sh '''
          git pull origin main
        '''
      }
    }
    stage('Testing script') {
      steps {
        echo "This is build number $BUILD_NUMBER of $COURSE"
        sh '''
               echo "Using a multi-line shell step"
               chmod +x test_script.sh
               ./test_script.sh
            '''
        sleep 3
      }
    }

  }
  environment {
    COURSE = 'Calgary DevOps'
  }
}
