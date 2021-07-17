pipeline {
  agent any
  stages {
    stage('stage-1') {
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

    stage('') {
      steps {
        ansiblePlaybook(playbook: 'second_playbook.yml', become: true, inventory: 'inventory')
      }
    }

  }
  environment {
    COURSE = 'Calgary DevOps'
  }
}