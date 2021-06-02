pipeline {
   agent any
   
   environment {
       TECH_STACK="DEFAULT"
   }

   stages {
      stage('Tech') {
         steps {
            script{
              
              test = input message: 'Please select the Tech Stack to proceed', ok: 'OK',parameters: [choice(name: 'RELEASE_SCOPE', choices: 'JAVA\nPL-SQL', description: '')]
               
            }
            echo "${env.TECH_STACK}"
            echo test
         }
      }
   }
}
