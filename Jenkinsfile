pipeline {
  agent none
  options { 
    buildDiscarder(logRotator(numToKeepStr: '2'))
    skipDefaultCheckout true
  }
  stages {
    stage('Test-linux') {
      agent {
        kubernetes {
          label 'nodejs-pod'
          yamlFile 'linux/nodejs-pod.yaml'
        }
      }
      steps {
        checkout scm
        container('nodejs') {
          echo 'Hello World!'   
          sh 'node --version'
        }
      }
    }    
  }
}

