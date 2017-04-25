node {
    stage('Checkout') {
        checkout scm
    }

    stage('Compile') {
        sh 'mvn clean compile'
    }

    stage 'Static Analysis' {
        parallel(
                Checkstyle: {
                    node {
                        echo 'Running checkstyle'
                    }
                },
                Huntbugs: {
                    node {
                        echo 'Running huntbugs'
                    }
                },
                PMD: {
                    node {
                        echo 'Running huntbugs'
                    }
                },
                Findbugs: {
                    node {
                        echo 'Running huntbugs'
                    }
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
