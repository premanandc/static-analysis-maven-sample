
@NonCPS
def staticAnalysisJobs() {
    def staticAnalysisChecks = [checkstyle: 'Checkstyle', findbugs: 'Findbugs', 'huntbugs': 'Huntbugs']

    staticAnalysisChecks.collect { checks ->
        def jobs = [:]
        jobs[checks.value] = {
            return {
                node {
                    echo checks.key
                }
            }
        }
        jobs
    }
}

// Take the string and echo it.
def transformIntoStep(inputString) {
    // We need to wrap what we return in a Groovy closure, or else it's invoked
    // when this method is called, not when we pass it to parallel.
    // To do this, you need to wrap the code below in { }, and either return
    // that explicitly, or use { -> } syntax.
    return {
        node {
            echo inputString
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

    def stringsToEcho = ["a", "b", "c", "d"]

// The map we'll store the parallel steps in before executing them.
    def stepsForParallel = [:]

// The standard 'for (String s: stringsToEcho)' syntax also doesn't work, so we
// need to use old school 'for (int i = 0...)' style for loops.
    for (int i = 0; i < stringsToEcho.size(); i++) {
        // Get the actual string here.
        def s = stringsToEcho.get(i)

        // Transform that into a step and add the step to the map as the value, with
        // a name for the parallel step as the key. Here, we'll just use something
        // like "echoing (string)"
        def stepName = "echoing ${s}"

        stepsForParallel[stepName] = transformIntoStep(s)
    }

// Actually run the steps in parallel - parallel takes a map as an argument,
// hence the above.
    parallel stepsForParallel

    stage('Test') {
        sh 'mvn test'
    }

    stage('Package') {
        sh 'mvn package -Dmaven.test.skip'
    }
}
