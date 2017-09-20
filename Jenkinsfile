node{
    
      stage('Clone the Source Code') {
       echo 'cloning..'
       git credentialsId: 'github-credential', url: 'https://github.com/Chariotern/ui_maven_project.git'

      }
      stage('Compile & Package & Unit Test'){
          echo 'compiling the source code and package'
          echo 'Run unit test cases against the compiled source code'
          sh 'mvn clean compile package'

      }
      stage('Deploy Artifacts'){
          echo 'Deploy snapshots to artifactory repository'
          archiveArtifacts 'target/*.jar'
      }
      stage('Deploy to Dev'){
          echo 'Deploying artifactory to Dev environment'
          echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
      }
   
   //input 'Approval is require to push to Next Environment'

      stage('Deploy to Test'){
          echo 'Deploying to Test Environment'
          echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
      }
   

}
