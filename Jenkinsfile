pipeline {
  agent { label 'jenkins-slave' }
  tools {
    jdk 'jdk17'
    maven 'maven33'
  }
  environment {
    SCANNER_HOME = tool 'sonar-scanner'
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
    stage('Code Compile') {
      steps {
         //  compile code using Maven Tool
          sh 'mvn compile -DskipTests=true'   
      }
    }
    stage('Code build') {
      steps {
         //  Build the code using Maven Tool
          sh 'mvn clean package -DskipTests=true'   
      }
    }
    stage('Code analysis') {
      steps {
         //  Analyze the code using Sonarqube
           withSonarQubeEnv('sonarqube-server') {
                sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Ekart \
                       -Dsonar.java.binaries=. \
                       -Dsonar.projectKey=Ekart '''
           }   
      }
    }
  }
}
