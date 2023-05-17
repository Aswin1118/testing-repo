pipeline {
    agent {
        label 'agent-node'
    }

    stages {
        
        stage('Clone') {
            steps {
                dir("/home/ubuntu/workspace/test/petclinic/"){
                git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
            }
            }
        }

        stage('Test') {
            steps {
                timeout(time: 15, unit: 'MINUTES') {
                    dir("/home/ubuntu/workspace/test/petclinic/") {
                        sh 'mvn test'
                    }
                }
            }
            post {
                success {
                    slackSend(channel: 'https://app.slack.com/huddle/T049B5GKSP4/C057XG4UKEF', color: 'good', message: 'Tests passed successfully!')
                }
                failure {
                    slackSend(channel: 'https://app.slack.com/huddle/T049B5GKSP4/C057XG4UKEF', color: 'danger', message: 'Tests failed!')
                }
            }
        }
    }
}