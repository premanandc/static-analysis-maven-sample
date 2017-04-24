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

    def jobNames = ["Checkstyle", "Huntbugs", "Findbugs", "CPD"]

    def stepsForParallel = [:]

    for (int i = 0; i < jobNames.size(); i++) {
        def s = jobNames.get(i)
        def stepName = "${s}"

        stepsForParallel[stepName] = transformIntoStep(s)
    }

    parallel stepsForParallel

    stage('Test') {
        sh 'mvn test'
    }

    stage('Package') {
        sh 'mvn package -Dmaven.test.skip'
    }
}
