pipeline {
    agent any
    tools {
        maven 'maven-3.5.0'
    }
    stages {
        stage('Compile') {
            steps {
                echo 'Compiling...'
                sh 'mvn clean compile'
            }
        }
        stage('Unit Test') {
            steps {
                echo 'Unit Testing...'
                sh 'mvn test'
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