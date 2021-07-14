pipeline {
   agent any
   
   environment {
       COURSE='Calgary DevOps'
   }

   stages {
      stage('stage-1') {
         steps {
            echo "This is build number $BUILD_NUMBER of demo $COURSE"
            sh '''
               echo "Using a multi-line shell step"
               chmod +x test_script.sh
               ./test_script.sh
            '''
         }
      }
   }
}
