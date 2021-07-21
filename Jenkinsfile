pipeline {
  agent any
  stages {
    state('Audit Tool') {
      steps {
         sh '''
            git --version
            ansible --version
            node --version
            npm --version
         '''
      }
    }
    stage('testing') {
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
