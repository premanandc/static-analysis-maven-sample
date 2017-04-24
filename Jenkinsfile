node {
    stage('Checkout') {
        checkout scm
    }

    stage('Compile') {
        sh 'mvn clean compile'
    }

    stage('Test') {
        sh 'mvn test'
    }
}
