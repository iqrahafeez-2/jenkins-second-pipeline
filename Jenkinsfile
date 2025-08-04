pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
    }

    post {
        success {
            slackSend(channel: '#all-spsnet-internee', message: "✅ Build Successful - ${env.JOB_NAME} [#${env.BUILD_NUMBER}]")
        }
        failure {
            slackSend(channel: '#all-spsnet-internee', message: "❌ Build Failed - ${env.JOB_NAME} [#${env.BUILD_NUMBER}]")
        }
    }
}
