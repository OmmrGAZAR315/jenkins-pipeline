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
                            try {


                                // Check if there are changes
//                                 def changes = currentBuild.changeSets
                                if (true) {
                                    echo 'There are changes in the repository!'
                                def changeLog = sh(script: 'git log --pretty=format:"%h - %an, %ar : %s"', returnStdout: true).trim()

                                    echo "Changes in this build:"
                                    echo "${changeLog}"
                                } else {
                                    echo 'No changes detected. Skipping delivery.'
                                }
                            } catch (Exception e) {
                                echo "Error occurred: ${e.message}"
                            }
                        }
                    }
                }
    }
}
