pipeline {
  agent any
  stages {
    stage('Build') {
      environment {
        SQL_CRED = credentials('MYSQL_PASSWORD')
      }
      steps {
        echo 'Hello World'
        sh 'printenv'
      }
    }

    stage('Example') {
      when {
        anyOf {
          branch 'master'
          branch 'staging'
        }

      }
      input {
        message 'Should we continue?'
        id 'Yes, we should.'
        submitter 'alice,bob'
        parameters {
          string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        }
      }
      steps {
        echo "Hello ${params.PERSON}"
        echo "Biography: ${params.BIOGRAPHY}"
        echo "Toggle: ${params.TOGGLE}"
        echo "Choice: ${params.CHOICE}"
        echo "Password: ${params.PASSWORD}"
      }
    }

  }
  environment {
    CC = 'clang'
  }
  post {
    always {
      echo 'I will always say Hello again!'
    }

  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '1'))
    disableConcurrentBuilds()
    disableResume()
    preserveStashes(buildCount: 5)
    quietPeriod(15)
    retry(3)
    skipStagesAfterUnstable()
    timeout(time: 10, unit: 'SECONDS')
    timestamps()
  }
  parameters {
    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
  }
}