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
    stage('Deploy') {
      input {
            message "Should we continue?"
            ok "Deploy"
            parameters {
                choice(name: 'APP_VERSION', choices: "v1.1\nv1.2\nv1.3", description: 'What to deploy?')
            }
        }
      steps {
        echo "Deploying ${APP_VERSION}"
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
}
