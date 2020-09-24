pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage("checkout") {
            steps {
            
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/learneriq/spring3hibernate.git']]])
            }
        }
         stage("Build") {
            steps {
            sh "mvn clean package "
            }
                
        }
         stage("findbug") {
             steps {
                findbugs canComputeNew: false, defaultEncoding: '', excludePattern: '', healthy: '', includePattern: '', pattern: '', unHealthy: ''

             }
             }
         stage("checkstyle") {
             steps {
                        checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
             }
        }
         stage("pmd") {
             steps {
             pmd canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
             }
        }
    }
}
