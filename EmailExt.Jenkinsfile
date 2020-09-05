def recipients = "ashish60808@gmail.com,ashish60808@outlook.com" //multiple email are defined here
pipeline {

    agent {
            label '<agentname>'
          }

    stages {
        stage('passing the stage') {
            steps {
               sh "echo hello"
            }
        }

        stage('intentionally failing the stage') {
            steps {
               sh "! echo $?" //negating the status command
            }
        }
    }

    post {
         always {
             script{
            emailext (
                    body: '''${SCRIPT, template="groovy-html.template"}''',
                    subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
                    mimeType: 'text/html',
                    to: recipients //calling the recipients defined variables.
                    )
            }
    }

    }
}
