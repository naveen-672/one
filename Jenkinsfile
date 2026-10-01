@Library('jenkins_shared_library') _

pipeline {
    agent any
    tools {
        maven "mymaven"
    }
    stages {
        stage ("build") {
            steps {
                mavenBuild()
            }
        }
        stage ("build image") {
            steps {
                dockerImage("naveenkumar30/shared_library")
            }
        }
        stage ("image scan") {
            steps {
                trivyScan("naveenkumar30/shared_library")
            }
        }
        stage ("push to registry") {
            steps {
                pushToRegistry("naveenkumar30/shared_library")
            }
        }
    }
}
