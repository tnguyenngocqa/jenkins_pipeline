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
        stage('Example') {
            steps {
                echo "JENKINS_USER ${USERNAME}"
                echo "JENKINS_PASS ${PASSWORD}"
                echo "${params.Greeting} World!"
                echo "Fracis is running build id ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
    }
}
