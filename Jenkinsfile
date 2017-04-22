pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                echo 'Compiling...'
            }
            steps {
                echo 'Testing...'
            }
            steps {
                echo 'Packaging...'
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello again!'
        }
    }
}