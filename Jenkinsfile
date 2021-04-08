pipeline {
     agent { label 'jenkinslave1' }
     stages {
          stage("clone code") {
               steps {
                    git 'https://github.com/datsys96/task5nodejs.git'
               }
          }
          stage("build image") {
               steps {
                    sh 'docker build -t nodejs12:2 .'
               }
          }
     }

    post {
        always {
	emailext body: 'helle day la jenkin nha', subject: 'test jenkin', to: 'datbeo12c@gmail.com'
        }
	        success {
            emailext body: 'ok ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
        unstable {
            emailext body: 'unstable ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
        failure {
            emailext body: 'failure ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: '$datbeo12c@gmail.com'
        }
        changed {
            emailext body: 'change ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
    }
}
