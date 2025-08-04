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
        sh """
        curl -X POST -H 'Content-type: application/json' \
        --data '{"text":"✅ Build Successful - jenkins-second-pipeline [#${BUILD_NUMBER}]"}' \
        https://hooks.slack.com/services/your/webhook/url
        """
    }
    failure {
        sh """
        curl -X POST -H 'Content-type: application/json' \
        --data '{"text":"❌ Build Failed - jenkins-second-pipeline [#${BUILD_NUMBER}]"}' \
        https://hooks.slack.com/services/your/webhook/url
        """
    }
}
}

// Testing webhook trigger
