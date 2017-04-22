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
        success {
            echo "Build success!"
        }
        always {
            echo 'All done!'
        }
    }
}