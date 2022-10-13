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
  tool {shiningpanda "phyton"}
  stage('Unit Testing') {
      steps {
        script {
          sh """
          python -m unittest discover -s tests/unit
          """
        }
      }
    }
}
