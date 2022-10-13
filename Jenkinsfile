node {
  stage('SCM') {
    checkout scm
  }
  
  stage('Build') {
        git 'https://github.com/katiagsoto/DOTT.git'
  }    
  
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonarqubescanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
  
  stage('Test') {
    git 'https://github.com/katiagsoto/DOTT.git'
      script {
         try {
         //Move to the correct directory
         sh 'cd /$WORKSPACE/'
         //Make sure all of the necessary libraries and plug-ins are installed
         sh 'sudo apt install python3-pip'
         sh 'sudo python3 -m pip install pytest'
         //Execute test in verbose format
         sh 'pytest tests.py -v'
         }
         catch (exc) {
         echo 'Unit tests failed'
    }
  }
}           
