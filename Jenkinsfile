pipeline {
    agent any

    stages {
        stage('Init') {
            steps {
                checkout scm
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
                def nextVersion = getNextSemanticVersion()
                sh "git tag ${nextVersion}"
                sh "git push origin ${nextVersion}"
                echo 'Deploying....'
            }
        }
    }
}