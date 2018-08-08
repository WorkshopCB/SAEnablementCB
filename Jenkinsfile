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
    stage('Testing'){
      failFast true
      parallel {
        stage('Java8'){
          agent { label 'jdk8'}
          steps{
            sh 'java -version'
            sleep time: 10, unit: 'SECONDS'
          }
        }
        stage('Java9'){
          agent { label 'jdk9' }
          steps {
            sh 'java -version'
            sleep time: 20, unit: 'SECONDS'
          }
        }
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
