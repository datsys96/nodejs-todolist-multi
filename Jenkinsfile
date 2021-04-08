pipeline {
     agent { label 'jenkinslave1' }
     stages {
          stage("clone code") {
               steps {
                    git 'https://github.com/datsys96/task5nodejs.git'
               }
          }
	   stage("sona scaner") {
               steps {
               withSonarQubeEnv('sonar') {
                sh "${scannerHome}/bin/sonar-scanner"
               }
                waitForQualityGate abortPipeline: true
          }
          }
          stage("test junit") {
               steps {
                    junit 'test.xml'
               }
          }
     }

    post {
        always {
	emailext body: 'helle day la jenkin nha', subject: 'test jenkin', to: 'tuandatithubt@gmail.com'
        }
	        success {
            emailext body: 'ok ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
        unstable {
            emailext body: 'unstable ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
        failure {
            emailext body: 'failure ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
        changed {
            emailext body: 'change ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
    }
}
