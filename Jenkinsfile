pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo "Hell0 ${MY_NAME}!"
        sh 'java -version'
      }
    }
  }
  environment {
    MY_NAME = 'Mary'
  }
}