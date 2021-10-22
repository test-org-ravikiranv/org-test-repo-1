pipeline {
  agent any
  
  tools 
    {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }
  
  stages {
    
    stage('SCM') {
      steps {
        git(url: 'https://github.com/ravikirankiran097/Spring-PetClinic.git', branch: 'main', credentialsId: 'GitHub_Cred')
      }
    }

    stage('Build & Test') {
      steps {
        sh "mvn -Dmaven.test.failure.ignore=true -Dcheckstyle.skip clean package"
      }
    }

  }
}
