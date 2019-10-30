pipeline {
    agent any
    stages {
        stage('test') {
            steps {
                sh label:'prepare script', script: '''#!/bin/bash
# create UserData
echo ${BUILD_TAG}
'''
        
                sh script: "echo ${BUILD_TAG}", label: "my step"

            }
        }
    }
}