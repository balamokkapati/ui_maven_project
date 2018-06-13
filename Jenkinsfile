pipeline {
    agent any 
    stages {
        stage('Code Checkout') { 
            steps {
                // Provide git url to checkout using pipeline syntax.
              git credentialsId: 'Github', url: 'https://github.com/yegendhar/indianteam.git'
            }
        }
        stage('Build') { 
            steps {
                // Build using maven project
                  sh 'mvn clean compile' 
            }
        }
        stage('Test') { 
            steps {
                //Test execution through maven
                sh 'mvn test'  
            }
        }
        stage('Local Archive') { 
            steps {
                //
             sh 'mvn install'  
            }
        }
        stage('Deploy to Dev') { 
            steps {
                //
             sh 'mvn install'  
            }
        }
    }
}
