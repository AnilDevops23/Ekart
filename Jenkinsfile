pipeline {
  agent { label 'jenkins-slave' }
  tools {
    jdk 'jdk17'
    maven 'maven33'
  }
  stages {
    stage('Clean Workspace') {
      steps {
         //  clean before build
                cleanWs()
      }
    }
    stage('SCM Checkout') {
      steps {
         //  checkout the code from SCM
          git branch: 'main', credentialsId: 'github', url: 'https://github.com/AnilDevops23/Ekart.git'   
      }
    }
  }
}
