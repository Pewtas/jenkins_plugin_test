pipeline {
    agent any

    stages {
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