pipeline {
   agent {
        node {
            label 'docker-agent-python'
            }
      }
    triggers {
        pollSCM 'H/5 * * * *'
    }
    stages {
        stage('Checkout') {
                steps {
                    // Checkout the repository
                    checkout([
                    $class: 'GitSCM',
                     branches: [[name: '*/main']],
                     doGenerateSubmoduleConfigurations: false,
                     extensions: [],
                     submoduleCfg: [],
                     userRemoteConfigs: [[url: 'https://github.com/OmmrGAZAR315/jenkins-pipeline.git']]
                    ])
                }
            }
    stage ("Build"){
            steps {
                echo "Building The job"
                sh '''
                cd myapp
                pip install -r requirements.txt
                '''
            }
        }
        stage("Test"){
            steps {
                echo "Testing The job"
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name='DR.Youssef Senousy'
                '''
            }
        }
        stage('Deliver') {
            steps {
                script {
                    // Check if there are changes
                    def changes = currentBuild.changeSets
                    if (changes.size() > 0) {
                    echo 'There is changes in the repository!"
                     def changeLog = sh(script: 'git log --pretty=format:"%h - %an, %ar : %s"', returnStdout: true).trim()
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


