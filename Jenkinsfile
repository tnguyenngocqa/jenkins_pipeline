properties([pipelineTriggers([githubPush()])])
echo 'Wellcome to Github Webhook - I am dev-1 branch'
echo 'Wellcome to Github Webhook'
echo 'Wellcome to Github Webhook'
echo 'Wellcome to Github Webhook'
def username = 'Jenkins'
echo 'Hello Mr. ${username}'
echo "I said, Hello  Mr. ${username}"

pipeline {
    agent {
        label 'master'
    }
    environment {
        USERNAME = 'JENKINS_USER'
        PASSWORD = 'JENKINS_PASS'
    }
    parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the word?')
    }
    stages {
        stage('Stage 1') {
            steps {
                echo "JENKINS_USER ${USERNAME}"
                echo "JENKINS_PASS ${PASSWORD}"
                echo "${params.Greeting} World!"
                echo "Fracis is running build id ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo "JENKINS_USER ${USERNAME}"
                echo "JENKINS_PASS ${PASSWORD}"
                echo "${params.Greeting} World!"
                echo "Fracis is running build id ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo "JENKINS_USER ${USERNAME}"
                echo "JENKINS_PASS ${PASSWORD}"
                echo "${params.Greeting} World!"
                echo "Fracis is running build id ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
        stage('Stage 2') {
            steps {
                echo "JENKINS_USER ${USERNAME}"
                echo "JENKINS_PASS ${PASSWORD}"
                echo "${params.Greeting} World!"
                echo "Fracis is running build id ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
        stage('Stage 3') {
            steps {
                echo "JENKINS_USER ${USERNAME}"
                echo "JENKINS_PASS ${PASSWORD}"
                echo "${params.Greeting} World!"
                echo "Fracis is running build id ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }        
    }
}
stage('Unit Tests'){
    parallel linux: {
        node('master'){
            checkout scm
            try {
                echo 'start linux test'
            }
            finally {
                echo 'end linux test'
            }       
        }
    },
    windows: {
        node('master'){
            checkout scm
            try {
                echo 'start windows test'
            }
            finally {
                echo 'end windows test'
            }       
        }
    }
}
stage('Integration Tests'){
    parallel linux: {
        node('master'){
            checkout scm
            try {
                echo 'start linux test'
            }
            finally {
                echo 'end linux test'
            }       
        }
    },
    windows: {
        node('master'){
            checkout scm
            try {
                echo 'start windows test'
            }
            finally {
                echo 'end windows test'
            }       
        }
    }
}
