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
          branch 'main'
          expression { env.TAG_NAME != env.BRANCH_NAME }
        }
      }
      steps {
        sh 'sonar-scanner -Dsonar.host.url=http://44.223.94.106:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=exp_frontend -Dsonar.qualitygate.wait=true'
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

  post {
    always {
    cleanWs()
    }
  }
}
