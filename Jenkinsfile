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
pipeline {
  agent any 
  stages {
    stage('build') {
      steps {
        sh 'python3 api.py'
      }
    }
    stage('test') {
      steps {
        sh 'python3 -m pytest'
      }   
    }
  }
}
