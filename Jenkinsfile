pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage("checkout") {
            steps {
            
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/opstree/spring3hibernate.git']]])
            }
        }
         stage("Build") {
             steps {
             sh "mvn -Dmaven.test.failure.ignore=true clean package"
             }
        }
         stage("findbug") {
             steps {
         checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/opstree/spring3hibernate.git']]])
        
             }
             }
         stage("checkstyle") {
             steps {
             checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/opstree/spring3hibernate.git']]])
             }
        }
         stage("pmd") {
             steps {
             pmd canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
             }
        }
    }
}
