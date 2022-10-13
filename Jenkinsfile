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
  stage('Unit Testing') { // Perform unit testing
      steps {
        script {
          sh """
          python -m unittest discover -s tests/unit
          """
        }
      }
    }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
