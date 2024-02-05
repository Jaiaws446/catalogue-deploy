pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    // environment { 
    //     packageVersion = ''
    //     nexusURL = '172.31.9.199:8081'
    // }
    options {
                timeout(time: 1, unit: 'HOURS')
                disableConcurrentBuilds()
    }
    parameters {
        string(name: 'version', defaultValue: '', description: 'What is the artifact version?')
        string(name: 'environment', defaultValue: 'dev', description: 'What is the environment?')
    }
    //build
    stages {
        stage('Print version') {
            steps {
                sh """
                    echo "version: ${params.version}"
                    echo "environment: ${params.environment}"
                """
            }
        }

        // stage('Print version') {
        //     steps {
        //         sh """
        //             echo "version: ${params.version}"
        //             echo "environment: ${params.environment}"
        //         """
        //     }
        // }

    }
    // post build
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }

        failure { 
            echo 'this runs when pipeline is failed, used genereally to send some alerts'
        }

        success { 
            echo 'I will say hello when pipeline is success'
        }
    }
}