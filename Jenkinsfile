#!/usr/bin/groovy
def gv
def pipeline

pipeline {
  agent any
  environment {
    NEW_VERSION = '1.3.0'
    // SERVER_CREDENTIALS = credentials('')
  }
  stages {
    stage("init"){
      steps{
        script {
           gv = load "pipeline.groovy"
           CODE_CHANGES = gv.getGitChanges()
        }
      }
    }
    stage("build"){
      when {
        expression {
          echo "building version ${CODE_CHANGES}"
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
