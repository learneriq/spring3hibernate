pipeline {
  agent any
  stages {
    stage('checkout') {
      parallel {
        stage('checkout') {
          steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/learneriq/spring3hibernate.git']]])
          }
        }

        stage('merge') {
          steps {
            echo 'hello'
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package '
      }
    }

    stage('findbug') {
      steps {
        findbugs()
      }
    }

    stage('checkstyle') {
      steps {
        checkstyle()
      }
    }

    stage('pmd') {
      steps {
        pmd()
      }
    }

  }
  tools {
    maven 'M3'
  }
}