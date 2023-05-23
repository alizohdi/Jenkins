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
    stage("init"){
      steps{
        //script {
        //}
      }
    }
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
        steps {
          echo 'send an email...'
        }
    }
    success {
        steps {
          echo 'send an email...'
        }
    }
    failure {
        steps {
          echo 'send an email...'
        }
    }
    aborted {
        steps {
          echo 'send an email...'
        }
    }
  }
}
