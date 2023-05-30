pipeline {
    agent {
        label 'Built-In Node'
    }

    stages {
        stage('Deploy') {
            steps{
                dir('/data/jenkins/workspace/java package'){
                    sh '''
                    curl -v -u aswin/nexus --upload-file spring-petclinic.jar \
                    http://35.91.111.112:8081/repository/petclinic-jarfile/org/springframework/boot/petclinic/3.0.7/petclinic-3.0.7.jar
                    '''
                }
            }
        }
    }
}