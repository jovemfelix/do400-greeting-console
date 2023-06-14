pipeline{
    agent{
        label "master"
    }
    stages{
        stage("Install dependencies"){
            steps{
                echo "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                echo "npm run lint"
            }
        }

        stage("Test"){
            steps{
                echo "npm test"
            }
        }

        stage('Release') {
            steps {
                sh '''
                    oc project developer-greetings
                    oc start-build greeting-console  --follow --wait
                '''
            }
        }
    }
}
