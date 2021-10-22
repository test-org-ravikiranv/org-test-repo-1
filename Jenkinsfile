pipeline {
  agent any
  stages {
    stage('Tools') {
      steps {
        tool(name: 'M3', type: 'maven')
      }
    }

    stage('') {
      steps {
        git(url: 'https://github.com/ravikirankiran097/Spring-PetClinic.git', branch: 'main', credentialsId: 'GitHub_Cred')
      }
    }

  }
}