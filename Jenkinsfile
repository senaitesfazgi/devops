pipeline {
  agent any
  environment {
    COURSE = 'Calgary DevOps'
    BRANCH = 'main'
  }
  stages {
    stage('Audit Tool') {
      steps {
        echo "Audit all tools versions" 
        sh '''
            git --version
            ansible --version
            node --version
            npm --version
            ng --version
         '''
         echo "Workspace: ${WORKSPACE}"
         echo "Workspace Temp: ${WORKSPACE_TMP}"
      }
    }
    stage('Get Source') {
      steps {
        sh 'git pull origin "${BRANCH}"'
      }
    }
    stage('Install Front-End Packages') {
      steps {
        sh 'cd "${WORKSPACE}/conduit-ui"'
        sh 'npm install'
      }
    }
    stage('Lint Front-End') {
      steps {
        sh 'cd "${WORKSPACE}/conduit-ui"'
        sh 'ng lint'
      }
    }
    stage('Test Front-End') {
      steps {
        sh 'cd "${WORKSPACE}/conduit-ui"'
        sh 'ng test'
      }
    }
    stage('Compile Front-End') {
      steps {
        sh 'cd "${WORKSPACE}/conduit-ui"'
        sh 'ng test'
      }
    }
  }
}
