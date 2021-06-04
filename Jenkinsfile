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
               
              def props = readFile 'C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\pipeline.properties'
             
              echo props
              
              if (TECH_STACK == 'JAVA'){
                 echo "JAVA --- daaaa"
                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: props]]])
              }
              else if(TECH_STACK == 'PL-SQL'){
               echo "PLSQL da ------- "
              }
           } 
        }
      }
      stage('Build '){
         steps{
            script{
               if (TECH_STACK == 'JAVA'){
                 echo "JAVA --- Built"
                 bat '''set MAVEN_HOME=C:\\Users\\Gary\\Downloads\\apache-maven-3.8.1-bin\\apache-maven-3.8.1
                     set JAVA_HOME=C:\\Program Files\\Java\\jdk1.8.0_291
                     set path=%MAVEN_HOME%\\bin;%PATH%
                     set path=%JAVA_HOME%\\bin;%PATH%
                     mvn sonar:sonar
                     mvn clean install'''
              }
              else if(TECH_STACK == 'PL-SQL'){
               echo "No Build for PL-SQL "
               echo  "${env.JOB_NAME}"
              }
            }
         }
      }

   }
}
