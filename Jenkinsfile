// properties = null

// def loadProperties() {
//     node {
//         checkout scm
//         properties = readProperties file: 'pipeline.properties'
//         echo "Immediate one ${properties.test}"
//     }
// }


pipeline {
   agent any
   
   environment {
       TECH_STACK=""
   }

   stages {
      stage('Tech-Stack') {
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
               
               def props = readJSON file: 'pipelineproperties.json'
              
              
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
