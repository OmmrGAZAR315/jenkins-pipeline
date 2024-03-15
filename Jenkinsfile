pipeline {
    agent any
    
    stages {
        // stage('Checkout') {
        //     steps {
        //         // Checkout the repository
        //         checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'your_repository_url']]])
        //     }
        // }
        
        stage('Display Changes') {
            steps {
                script {
                    // Use git commands to fetch changes
                    def changeLog = sh(script: 'git log --pretty=format:"%h - %an, %ar : %s"', returnStdout: true).trim()
                    echo "Changes in this build:"
                    echo "${changeLog}"
                }
            }
        }
    }
}
