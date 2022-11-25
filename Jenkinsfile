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
                    def nextVersion = getNextSemanticVersion majorPattern: '^[Mm]ajor.*',
                        minorPattern: '^[Ff]eature.*',
                        patchPattern: '^[Bb]ugfix.*'
                }
                echo "Deploying version ${nextVersion}"
            }
        }
    }
    post {
        success {
            script {
                sh "git tag ${nextVersion}"
                sh "git push origin ${nextVersion}"
            }
        }
    }
}