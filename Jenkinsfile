pipeline {
  agent {
    node {
      label 'jdk8'
    }

  }
  libraries {
    lib("SharedLibs")
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
    // stage('Testing'){
    //   failFast true
    //   parallel {
    //     stage('Java8'){
    //       agent { label 'jdk8'}
    //       steps{
    //         sh 'java -version'
    //         sleep time: 10, unit: 'SECONDS'
    //       }
    //     }
    //     stage('Java9'){
    //       agent { label 'jdk9' }
    //       steps {
    //         sh 'java -version'
    //         sleep time: 20, unit: 'SECONDS'
    //       }
    //     }
    //   }
    // }
    stage('Testing') {
        parallel {
          stage('Java 8') {
            agent { label 'jdk9' }
            steps {
              container('maven8') {
                sh 'mvn -v'
              }
            }
          }
          stage('Java 9') {
            agent { label 'jdk8' }
            steps {
              container('maven9') {
                sh 'mvn -v'
              }
            }
          }
        }
      }
    stage('Checkpoint'){
      agent none
      steps {
        checkpoint 'Checkpoint'
      }
    }
    stage('Deploy'){
      agent none
      steps {
        echo "Deploying..."
      }
    }
    stage('Shared Lib'){
      steps{
        helloWorld("Jenkins")
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
