@NonCPS
def staticAnalysisJobs() {
    def staticAnalysisChecks = [checkstyle: 'Checkstyle', findbugs: 'Findbugs', 'huntbugs': 'Huntbugs']

    staticAnalysisChecks.collect { checks ->
        def jobs = [:]
        jobs[checks.value] = {return { build checks.key }}
        jobs
    }
}

node {
    stage('Checkout') {
        checkout scm
    }

    stage('Compile') {
        sh 'mvn clean compile'
    }


    parallel staticAnalysisJobs()

    stage('Test') {
        sh 'mvn test'
    }

    stage('Package') {
        sh 'mvn package -Dmaven.test.skip'
    }
}
