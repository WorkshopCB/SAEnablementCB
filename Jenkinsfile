pipeline {
  agent {
    node {
      label 'jdk8'
    }

  }
  stages {
    stage('Say Hello') {
      steps {
        echo "Hell0 ${params.Name}!"
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
        sh 'java -version'
      }
    }
  }
  environment {
    TEST_USER = credentials('test-user')
    MY_NAME = 'Mary'
  }
  parameters {
    string(name: 'Name', defaultValue: 'David', description: 'Who should I say hi to?')
  }
  post {
    aborted {
      echo "Why didn\'t you push the button?"
    }
  }
}
