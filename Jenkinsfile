pipeline {
  agent any

  stages {
    stage( 'Code Quality') {
      steps {
        //sh 'sonar-scanner -Dsonar.host.url=http://3.230.172.62:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=exp_frontend -Dsonar.qualitygate.wait=true'
        sh 'echo CQ'
      }
    }

    stage ( 'Unit Tests') {
      steps {
        sh ' echo Unit Tests'
      }
    }

    stage ( 'Release' ) {
      steps {
        sh 'docker build -t 492681564023.dkr.ecr.us-east-1.amazonaws.com/frontend:1.0.0 .'
        sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 492681564023.dkr.ecr.us-east-1.amazonaws.com'
        sh 'docker push 492681564023.dkr.ecr.us-east-1.amazonaws.com/frontend:1.0.0'
      }
    }
  }
}
