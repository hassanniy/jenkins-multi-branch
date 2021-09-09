pipeline {

    agent any

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {
       
        stage(' Unit Testing') {
            when { triggeredBy cause: "admin" }
            steps {
                sh """
                echo "Running Unit Tests"
                """
            }
        }

        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Deliver for development') {
        when {
                expression {
                    return env.gitlabBranch == 'develop'
                }
            }
            
            steps {
                sh 'your_filename_along_with_your_filepath'
                echo "Building Artifact for Development"
                
                
            }
        }
        
        stage('Deploy for staging') {
           when {
                expression {
                    return env.gitlabBranch == 'staging'
                }
            }
            
            steps {
                sh 'your_filename_along_with_your_filepath'
                echo "Building Artifact for Staging"
              
            }
        }
    
        }
       post {
        always {
            archiveArtifacts artifacts: '*.md'
        }
    }
       
}
