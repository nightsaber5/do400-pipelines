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
	    when { expression { params.RUN_FRONTEND_TESTS } }
        stage('Run Tests') {
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
            }
        }
    }
}