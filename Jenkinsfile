pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Starting the build process for the project.'
                echo 'mvn clean package' 
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Executing Unit and Integration Tests.'
                echo 'mvn test'
            }
            post {
                always {
                    mail to: 'junayedalam.au@gmail.com',
                         subject: "Unit and Integration Tests: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                         body: "The Unit and Integration Tests have been run. Please review the results."
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running static code analysis...'
                echo 'sonar-scanner -Dsonar.projectKey=my_project -Dsonar.sources=src'
            }
            post {
                always {
                    mail to: 'junayedalam.au@gmail.com',
                         subject: "Code Analysis: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                         body: "The code analysis has been completed. Please check the report."
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Conducting a security scan...'
                echo 'dependency-check.bat --project my_project --out . --scan ./src'
            }
            post {
                always {
                    mail to: 'junayedalam.au@gmail.com',
                         subject: "Security Scan: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                         body: "The security scan has been performed. Please check the results."
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to the Staging environment...'
                echo 'Copy-Item target'
            }
            post {
                always {
                    mail to: 'junayedalam.au@gmail.com',
                         subject: "Staging Deployment: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                         body: "The application has been deployed to the Staging environment. Please verify."
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Executing integration tests in the Staging environment...'
                echo 'Invoke-WebRequest -Uri http://staging-server/api/tests -UseBasicParsing'
            }
            post {
                always {
                    mail to: 'junayedalam.au@gmail.com',
                         subject: "Integration Tests on Staging: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                         body: "The integration tests on the Staging environment have been completed. Please review the outcomes."
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to the Production environment...'
                echo 'Copy-Item'
            }
            post {
                always {
                    mail to: 'junayedalam.au@gmail.com',
                         subject: "Production Deployment: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                         body: "The application has been successfully deployed to the Production environment. Please check."
                }
            }
        }
    }

    post {
        always {
            echo 'Performing cleanup operations...'
        }

        success {
            echo 'The pipeline was successful!'
            mail to: 'junayedalam.au@gmail.com',
                 subject: "SUCCESS: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                 body: "The entire pipeline completed successfully."
        }

        failure {
            echo 'The pipeline encountered a failure.'
            mail to: 'junayedalam.au@gmail.com',
                 subject: "FAILURE: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                 body: "The pipeline failed. Please review the logs for details."
        }
    }
}
