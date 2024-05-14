pipeline {
    agent any
    tools { 
        maven 'mvn' 
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Desploy to Staging') {
            steps {
                build job: 'Deploy-to-staging'
            }
        }    
    }    
}
