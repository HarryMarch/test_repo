pipeline {
    agent any
    stages {
        stage('test') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'src']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GerritHRBC', url: 'ssh://gerrit.ps.porters.local/search/ami/index-worker']]])
                sh label:'prepare script', script: '''#!/bin/bash
# create UserData
cp src/ami.env out
'''
        
                sh script: "echo ${BUILD_TAG}", label: "my step"
                stash includes: 'out/**', name: 'out'
                stash includes: 'tools/build/build-ami.sh', name: 'tools'
            }
        }
    }
}