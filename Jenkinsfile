pipeline {
   agent any
   
   environment {
       TECH_STACK=""
   }

   stages {
      stage('Tech') {
         steps {
            script{
              
              TECH_STACK = input message: 'Please select the Tech Stack to proceed', ok: 'OK',parameters: [choice(name: 'Java / PLSQL', choices: 'JAVA\nPL-SQL', description: '')]
               
            }
            echo "${TECH_STACK}"
            
         }
      }
      stage('CheckOut') {
        steps{
           script{
              if (TECH_STACK == 'JAVA'){
                 echo "JAVA --- daaaa"
              }
              else if(TECH_STACK == 'PLSQL'){
               echo "PLSQL da ------- "
              }
           }
        }
      }
   }
}
