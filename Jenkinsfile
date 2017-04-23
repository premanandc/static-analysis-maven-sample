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
        stage('Integration Test') {
            steps {
                script {
                    def browsers = ['chrome', 'firefox']
                    for (int i = 0; i < browsers.size(); ++i) {
                        echo "Testing the ${browsers[i]} browser"
                    }
                }
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