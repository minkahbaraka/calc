pipeline {
    agent any
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
                sh "gradle ./JacocoTestReport "
                sh "gradle ./JacocoTestCoverageVerification "
            }
        }
    }
}