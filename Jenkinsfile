pipeline {
    agent any

    stages {
        stage('configure git') {
            steps {
                sh 'git config --global user.email "jenkins.test@test.de"'
                sh 'git config --global user.name "jenkins"'
                sh 'git config --global credential.helper cache'
                sh "git config --global credential.helper 'cache --timeout=3600'"
                script {
                    git credentialsId: 'jenkins_final', url: 'https://github.com/Pewtas/jenkins_plugin_test.git', branch: env.BRANCH_NAME
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def nextVersion = getNextSemanticVersion()
                    sh "git tag ${nextVersion}"
                    sh "git push origin ${nextVersion}"
                }
                echo 'Deploying...'
            }
        }
    }
}