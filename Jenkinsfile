@Library('jenkins_shared_library')

pipeline {
    agent any
    stages {
        stage ("clean workspace") {
            steps {
                cleanWorkspace()
            }
        }
        stage ("checkout") {
            steps {
                checkout("master", "https://github.com/naveen-672/one.git")
            }
        }
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
