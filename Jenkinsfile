pipeline {
    agent any
    stages {
        stage('test') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'src']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'none', url: 'shttps://github.com/HarryMarch/test_repo']]])

                sh label:'prepare script', script: '''#!/bin/bash
# create UserData
echo ${BUILD_TAG}
echo src/ami.env
'''

                sh script: "echo ${BUILD_TAG}", label: "my step"
            }
        }
    }
}