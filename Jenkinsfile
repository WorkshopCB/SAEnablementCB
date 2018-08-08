pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo "Hell0 ${MY_NAME}!"
        echo "${TEST_USER}"
        echo "${TEST_PWD}"
        sh 'java -version'
      }
    }
  }
  environment {
    TEST_USER = credentials('test-user')
    MY_NAME = 'Mary'
  }
}