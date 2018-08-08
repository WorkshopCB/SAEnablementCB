pipeline {
  agent {
    node {
      label 'jdk9'
    }

  }
  stages {
    stage('Say Hello') {
      agent {
        node {
          label 'jdk9'
        }

      }
      steps {
        echo 'Hell0 W0rld!'
        sh 'java -version'
      }
    }
  }
}