pipeline {
    agent any
    
    stages {
        // stage('Checkout') {
        //     steps {
        //         // Checkout the repository
        //         checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'your_repository_url']]])
        //     }
        // }
        
        stage('Deliver') {
                    steps {
                        script {
                            // Check if there are changes
                            def changes = currentBuild.changeSets
                            if (true) {
                            def changeLog = sh(script: 'git log --pretty=format:"%h - %an, %ar : %s"', returnStdout: true).trim()
                                echo 'There are changes in the repository!'
                                echo "Changes in this build:"
                                echo "${changeLog}"
                            } else {
                                echo 'No changes detected. Skipping delivery.'
                            }
                        }
                    }
                }
    }
}
