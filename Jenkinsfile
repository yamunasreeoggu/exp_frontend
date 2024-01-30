pipeline {
  agent {
    node { label 'workstation' }
  }

  options {
    ansiColor('xterm')
  }

  stages {
    stage( 'Code Quality') {
      when {
        allOf {
          expression { env.TAG_NAME != env.BRANCH_NAME }
        }
      }
      steps {
        sh 'sonar-scanner -Dsonar.host.url=http://3.230.172.62:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=exp_frontend -Dsonar.qualitygate.wait=true'
      }
    }

    stage ( 'Unit Tests') {
      when {
        allOf {
         branch 'main'
         expression { env.TAG_NAME != env.GIT_BRANCH }
        }
      }
      steps {
        sh ' echo Unit Tests'
      }
    }

    stage ( 'Release' ) {
      when {
        expression { env.TAG_NAME ==~ ".*" }
      }
      steps {
        sh 'echo CI'
      }
    }
  }
}
