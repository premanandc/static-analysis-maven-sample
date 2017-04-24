@NonCPS
def staticAnalysisJobs() {
    def staticAnalysisChecks = [checkstyle: 'Checkstyle', findbugs: 'Findbugs', 'huntbugs': 'Huntbugs']

    staticAnalysisChecks.collect { return {
        build it.key
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


    parallel staticAnalysisJobs

    stage('Test') {
        sh 'mvn test'
    }

    stage('Package') {
        sh 'mvn package -Dmaven.test.skip'
    }
}
