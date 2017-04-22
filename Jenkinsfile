pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                echo 'Compiling...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello again!'
        }
    }
}