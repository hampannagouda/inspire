pipeline {

    agent any

    parameters {
        choice(
            name: 'ACTION',
            choices: ['DEPLOY', 'REMOVE'],
            description: 'Deploy or Remove Website'
        )
    }

    stages {

        stage('Deploy Website') {

            when {
                expression {
                    params.ACTION == 'DEPLOY'
                }
            }

            steps {

                sh '''
                docker compose up --build -d
                '''
            }
        }

        stage('Remove Website') {

            when {
                expression {
                    params.ACTION == 'REMOVE'
                }
            }

            steps {

                sh '''
                docker compose down
                '''
            }
        }
    }

    post {

        success {
            echo 'Deployment Successful'
        }

        failure {
            echo 'Deployment Failed'
        }
    }
}