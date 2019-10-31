// Poll SCM (poll Source Control Management): ở trigger này sẽ lắng nghe repository của chúng ta nếu có thay đổi thì sẽ tự động call mục này để chỉ định chạy job của chúng ta. về cách setup cũng tương tự như Build periodically cũng gồm 5 mục

// MINUTES   phút trong một giờ (0-59)
// HOURS  giờ trong 1 ngày (0-23)
// DAY MONTH:  ngày trong tháng (0-31)
// MONTH tháng trong năm (1-12)
// DAYWEEK : ngày trong tuần (0-7) tương đương thứ 2 – chủ nhật

//properties([pipelineTriggers([githubPush()])])
properties([pipelineTriggers([pollSCM('* * * * *')])])

echo 'Wellcome to Github Webhook'
echo 'I am a dev'
echo 'I am a qa'
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
stage('Signoff'){
    node('master'){
        def condition = input("Deploy that to prod ?")
        echo 'condition is ${condition}'
        milestone()
    }
}
stage('Deploy to production'){
    node('master'){
        echo 'Deployed to production'
    }
}
