pipeline {
    agent {
        node {
            label 'nodejs'
        }
		}
    parameters {
        booleanParam(name: "RUN_FRONTEND_TESTS", defaultValue: true)
    }
    stages {
        stage('Run Tests') {
	    when { expression { params.RUN_FRONTEND_TESTS } }
            parallel {
                stage('Backend Tests') {
                    steps {
                        sh 'node ./backend/test.js'
                    }
                }
                stage('Frontend Tests') {
                    steps {
                        sh 'node ./frontend/test.js'
                    }
                }
				stage('Deploy') {
					when {
						expression { env.GIT_BRANCH == 'origin/main' }
						beforeInput true
					}
					input {
						message 'Deploy the application?'
					}					
					steps {
						echo 'Deploying...'
					}
				}				
            }
        }
    }
}