pipeline {
     agent any
     stages {
          stage('Clone the Source Code') {
               steps {
                 echo 'cloning..'
                 git credentialsId: 'github-credential', url: 'https://github.com/Chariotern/ui_maven_project.git'
            }
           
          }
         
          stage('Compile & Package & Unit Test'){
               steps {
                    echo 'compiling the source code and package'
                    echo 'Run unit test cases against the compiled source code'
                    sh 'mvn clean compile package'
                    }
            }

          stage('Deploy Artifacts'){
              echo 'Deploy snapshots to artifactory repository'
              archiveArtifacts 'target/*.jar'
              }
         
          stage('Deploy to Dev'){
               steps {
              echo 'Deploying artifactory to Dev environment'
              echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
              }
          }
   
   //input 'Approval is require to push to Next Environment'
          stage('Deploy to Test'){
               steps {
              echo 'Deploying to Test Environment'
              echo "${env.BUILD_ID}"
              }
          }
         }
      post { 
        always { 
            echo 'I will always say Hello again!'
        }
      }
    
}
