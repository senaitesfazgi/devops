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
        dir("${WORKSPACE}/conduit-ui") {
		  sh 'npm install'
        }
      }
    }
    stage('Lint Front-End') {
      steps {
        dir("${WORKSPACE}/conduit-ui") {
          sh 'npm run lint'
        }
      }
    }
    stage('Test Front-End') {
      steps {
        dir("${WORKSPACE}/conduit-ui") {
		  echo "Test can not be run cuz it tries to lauch the browser"
		  echo "sh 'npm run test'"
        }
      }
    }
    stage('Compile Front-End') {
      steps {
        dir("${WORKSPACE}/conduit-ui") {
		  sh 'npm run build'
        }
      }
    }
  }
}
