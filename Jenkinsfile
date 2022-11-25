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
                    sh "git tag --force ${nextVersion}"
                    sh "git push origin --force ${nextVersion}"
                }
                echo "Deploying...."
            }
        }
    }
}