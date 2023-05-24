#!/usr/bin/groovy

pipeline {
  parameters {
      choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'])
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
          echo "building version ${VERSION}"
          BRANCH_NAME == 'dev' && CODE_CHANGES == true
        }
      }
      steps {
        echo 'building the application...'
        echo "building version ${VERSION}"
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
      when {
        expression {
          params.VERSION == '1.2.0'
        }
      }
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
        emailext body: 'Email sent from Jenkins for Job's failure', subject: 'Test Email', to: 'ali.tehrani@equifax.com'
    }
    aborted {
        echo 'send an email on aborted...'
        emailext body: 'Email sent from Jenkins for Job's aborted', subject: 'Test Email', to: 'ali.tehrani@equifax.com'
    }
  }
}
