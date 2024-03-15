pipeline {
    agent any

    stages {
            stage('Checkout') {
            steps {
                // Checkout the repository
                checkout([
                $class: 'GitSCM',
                 branches: [[name: '*/master']],
                 doGenerateSubmoduleConfigurations: false,
                 extensions: [],
                 submoduleCfg: [],
                 userRemoteConfigs: [[url: 'https://github.com/OmmrGAZAR315/jenkins-pipeline.git']]
                ])
            }
        }

        stage('Display Changes') {
            steps {
                script {
                    // Get changes from the repository
                    def changeLog = sh(script: 'git log --pretty=format:"%h - %an, %ar : %s"', returnStdout: true).trim()
                    echo "Changes in this build:"
                    echo "${changeLog}"
                }
            }
        }
    }
}


