properties([pipelineTriggers([githubPush()])])

// Get repo information
def myRepo = checkout scm
def gitCommit = myRepo.GIT_COMMIT
def gitBranch = myRepo.GIT_BRANCH
def shortGitCommit = "v-${gitCommit[0..6]}"
// Agent Host IPs
def ipDeployMachine = "10.20.34.104"

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
        stage('Build') {
            steps {
                echo "JENKINS_USER ${USERNAME}"
                echo "JENKINS_PASS ${PASSWORD}"
                echo "${params.Greeting} World!"
                echo "Fracis is running build id ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
    }
}
stage('Unit Test'){
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
