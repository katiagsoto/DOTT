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
  stages {
    stage('build') {
      steps {
        git 'https://github.com/katiagsoto/DOTT.git'
        sh 'python api.py'
      }
    }
     stage('test') {
      steps {
        sh 'python test.py'
