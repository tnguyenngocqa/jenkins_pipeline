def username = 'Jenkins'
echo 'Hello Mr. ${username}'
echo "I said, Hello  Mr. ${username}"
pipeline {
    agent {
        label 'master'
    }
    parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the word?')
    }
    stages {
        stage('Example') {
            steps {
                echo "${params.Greeting} World!"
                echo "Fracis is running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
    }
}
