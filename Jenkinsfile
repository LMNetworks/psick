pipeline {
  agent any
  stages {
    stage('Syntax') {
      parallel {
        stage('Syntax') {
          steps {
            echo 'Syntax check'
            sh 'pdk validate'
          }
        }
        stage('Lint') {
          steps {
            echo 'Lint'
          }
        }
        stage('Chars') {
          steps {
            echo 'Chars'
            sh 'bin/puppet_check_syntax_fast.sh chars'
          }
        }
      }
    }
    stage('Unit') {
      steps {
        sh 'pdk  test unit'
      }
    }
    stage('Diff') {
      steps {
        sh 'bin/gitlab_catalog_preview.sh'
      }
    }
    stage('Integration') {
      steps {
        echo 'Integration'
      }
    }
  }
}