CODE_CHANGES == true
pipeline {
  agent any
  stages {
    stage("build"){
      when {
        expression {
          echo CODE_CHANGES
          BRANCH_NAME == 'dev' && CODE_CHANGES == true
        }
      }
      steps {
        echo 'building the application...'
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
