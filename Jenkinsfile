pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    
    stages{
        stage('Build') {
            steps {
                sh 'mvn clean install -f pom.xml'
            }
        }
        stage('Deploy on Docker') {
            steps {
               sshPublisher(publishers: [sshPublisherDesc(configName: 'docker-host', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ls', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: 'devsec-POC', remoteDirectorySDF: false, removePrefix: 'target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        }
    }
    }
}
