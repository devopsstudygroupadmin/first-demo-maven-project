pipeline {
  agent any
  tools {
    maven "maven_3.9.0"
  }

  stages {
        stage('Build Application') {
            steps {
                sh 'mvn clean install'
            }
          post {
            success {
              echo "Starting the archive process"
              archiveArtifacts artifacts: '**/*.war'
            }
          }
        }
        stage('Deploy Application') {
          steps {
            build job: 'APPLICATION-DEPLOYMENT-JOB'
          }
      
        }
    }
}
