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
  }
}