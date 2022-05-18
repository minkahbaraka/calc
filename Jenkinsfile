pipeline {
    agent any
    // triggers {
    //      pollSCM('* * * * *')
    // }
     // added comment here to test polling
     // added another comment to test polling since the above didn't work
     //after manual build this worked too good
    stages {
        stage ("Checkout") {
            steps {
                git url: 'https://github.com/minkahbaraka/calc.git'
            }
        }
        
        stage ("Compile") {
            steps {
                sh "./gradlew compileJava"
            }
        }
        
        stage ("Unit Test") {
            steps {
                sh "./gradlew test"
            }
        }

        stage ("Code Coverage") {
            steps {
                sh "./gradlew JacocoTestReport"

                // publishHTML (target: [
			        // reportDir: 'build/reports/jacoco/test/html',
			        // reportFiles: 'index.html',
			        // reportName: "JaCoCo Report"	
			        // ])
                // sh "./gradlew JacocoTestCoverageVerification "
            }
        }
    }
}

post {
		always {
			script {
				echo 'Post build'
			}
		}
		success {
			script {
				echo 'Success'
			}
		}
		aborted {
			script {
				echo 'Aborted'
			}
		}
		failure {
			script {
				echo 'Failure'
			}
		}
		cleanup {
		 	cleanWs()
        }
	}
