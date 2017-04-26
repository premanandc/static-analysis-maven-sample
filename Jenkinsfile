node {
    stage('Checkout') {
        checkout scm
    }

    stage('Compile') {
        sh 'mvn clean compile'
    }

    stage('Static Analysis') {
        parallel(
                Checkstyle: {
                    echo 'Running checkstyle'
                },
                Huntbugs: {
                    echo 'Running huntbugs'
                },
                PMD: {
                    echo 'Running PMD'
                },
                Findbugs: {
                    echo 'Running findbugs'
                }
        )
    }

    stage('Unit Test') {
        sh 'mvn test'
    }

    stage('Integration Test') {
        sh 'mvn integration-test'
    }

    stage('Package') {
        sh 'mvn package -Dmaven.test.skip'
    }
}
