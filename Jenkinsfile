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
}