pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                echo 'Compiling...'
            }
        }
        stage('Unit Test') {
            steps {
                echo 'Unit Testing...'
            }
            steps {
                echo 'More Unit Testing...'
            }
        }
    }
    post {
        success {
            echo "Build success!"
        }
        always {
            echo 'All done!'
        }
    }
}