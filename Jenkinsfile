pipeline {
    agent any

    environment {
        GIT_STUFF = credentials('jenkins_final')
    }

    stages {
        stage('configure git') {
            steps {
                checkout scm
                sh 'git config --global user.email "jenkins.test@test.de"'
                sh 'git config --global user.name "jenkins"'
                sh 'git remote set-url origin "https://"'
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