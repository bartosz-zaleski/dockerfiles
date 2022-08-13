pipeline {
  agent "docker"
  stages {
    stage('ubuntu') {
      steps {

        dir("ubuntu/") {
            sh (
                script: '''

docker build --tag jenkins/ubuntu:building .

docker images jenkins/ubuntu --format '{{.Tag}}'

// get the second-latest tag - most recent, apart from the latest
// tag++
// retag "latest" to the above
// retag "building" to "latest"
                '''
            )
        }
      }
    }

    stage('shellcheck') {
      steps {
        echo 'Hello world!'
      }
    }

    stage('rust') {
      steps {
        echo 'Hello world!'
      }
    }
  }
} 