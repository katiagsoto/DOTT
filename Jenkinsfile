node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonarqubescanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
agent any
stages {
    stage ('GIT Checkout'){
        steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/katiagsoto/DOTT.git']]])
        }
    }
    
    stage('build') {
  steps {
    sh 'python api.py'
  }
}
    stage ('Test'){
        steps {
            sh 'python -m pytest'
        }
    }
}
}
