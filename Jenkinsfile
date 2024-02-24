pipeline {
   agent {
        label 'agent-1'
    }
    // agent any
    environment{
        packageversion=''
    }
    parameters {
         booleanParam(name: 'deploy', defaultValue: false, description: 'Toggle this value')
    }


    options {
        timeout(time: 1, unit: 'HOURS') // Set a timeout for the entire pipeline
        ansiColor("xterm") 
        disableConcurrentBuilds()

    }

    stages {
        stage('Get version from Json file') {
            steps {
                script {
                     def jsonData = readJSON file: 'package.json'
                     packageversion=jsonData.version
                     echo "version : $packageversion"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo "Running tests..."
                    // Add your test steps here
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                   
                    // Add your deployment steps here
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully. Sending notification..."
            // Add notification steps for successful builds
        }

        failure {
            echo "Pipeline failed. Sending notification..."
            // Add notification steps for failed builds
        }

        always {
            echo "Cleaning up..."
            // Add any cleanup steps that should run regardless of success or failure
            deleteDir()
        }
    }
}
