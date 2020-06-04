pipeline {
  agent {
    docker {
      image 'maven:3.6.3-jdk-8'
    }

  }
  stages {
    stage('Initialize') {
      steps {
        sh '''echo PATH = ${PATH}
echo M2_HOME = ${M2_HOME}
mcn clean'''
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore=true install'
      }
    }

    stage('Report') {
      steps {
        junit 'report-results/'
        archiveArtifacts 'target/*.jar,target/*.hpi'
      }
    }

  }
}