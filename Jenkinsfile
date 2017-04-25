def transformIntoStep(inputString) {
    return {
        node {
            echo "Running $inputString"
        }
    }
}

node {
    stage('Checkout') {
        checkout scm
    }

    stage('Compile') {
        sh 'mvn clean compile'
    }

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
            })

    stage('Test') {
        sh 'mvn test'
    }

    stage('Package') {
        sh 'mvn package -Dmaven.test.skip'
    }
}
