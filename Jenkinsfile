pipeline {
  agent { label 'jenkins-slave' }
  tools {
    jdk 'jdk17'
    maven 'maven33'
  }
  stages {
    stage('Clean Workspace') {
      steps {
         //  Clean before build
                cleanWs()
      }
    }
  }
}
