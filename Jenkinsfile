pipeline {
    stages {
        stage('test') {
            steps {
                sh label:'prepare script', script: '''#!/bin/bash
# create UserData
cp src/ami.env out
'''
                sh script: "echo src/ami.env", label: "my step"
                stash includes: 'out/**', name: 'out'
                stash includes: 'tools/build/build-ami.sh', name: 'tools'
            }
        }
}