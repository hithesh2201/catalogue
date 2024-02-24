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

        stage('install dependencies') {
            steps {
                sh"""
                    npm install
                """
            }
        }

        stage('Build artifact') {
            steps {
                sh """
                    ls -ltr
                    zip -q -r catalogue.zip . -x "*.zip" -x ".git/*"
                    ls -ltr


            """
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
           
        }
    }
}
