#!/usr/bin/groovy

pipeline {
  parameters {
      booleanParam(name: 'dev', defaultValue: false, description: '...')
      booleanParam(name: 'qa', defaultValue: false, description: '...')
  }
  agent any
  //tools {
  //}
  environment {
    NEW_VERSION = '1.3.0'
    // SERVER_CREDENTIALS = credentials('')
  }
  stages {
      stage("build"){
      when {
        expression {
          echo "building version ${NEW_VERSION}"
          BRANCH_NAME == 'dev' && CODE_CHANGES == true
        }
      }
      steps {
        echo 'building the application...'
        echo "building version ${NEW_VERSION}"
      }
    }
    stage("test"){
      when {
        expression {
          BRANCH_NAME == 'dev'
        }
      }
      steps {
        echo 'testing the application...'
      }
    }
    stage("deploy"){
      steps {
        echo 'deploying the application...'
      }
    }
  }
  post {
    always {
        echo 'send an email always...'
    }
    success {
        echo 'send an email on success...'
    }
    failure {
        echo 'send an email on failure...'
    }
    aborted {
        echo 'send an email on aborted...'
    }
  }
}
