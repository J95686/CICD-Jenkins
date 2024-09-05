pipeline {
    agent any

    stages {
        
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Assuming using Maven for build automation
                // sh 'mvn clean package'
            }
            post {
                success {
                    emailext (
                        subject: "Build Successful",
                        body: "The Build stage completed successfully.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
                failure {
                    emailext (
                        subject: "Build Failed",
                        body: "The Build stage failed.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Assuming using JUnit for unit tests and Selenium for integration tests
                // sh 'mvn test'
                // sh 'mvn integration-test'
            }
            post {
                success {
                    emailext (
                        subject: "Unit and Integration Tests Successful",
                        body: "The Unit and Integration Tests stage completed successfully.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
                failure {
                    emailext (
                        subject: "Unit and Integration Tests Failed",
                        body: "The Unit and Integration Tests stage failed.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running Code Analysis...'
                // Assuming using SonarQube for code analysis
                // sh 'mvn sonar:sonar'
            }
            post {
                success {
                    emailext (
                        subject: "Code Analysis Successful",
                        body: "The Code Analysis stage completed successfully.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
                failure {
                    emailext (
                        subject: "Code Analysis Failed",
                        body: "The Code Analysis stage failed.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running Security Scan...'
                // Assuming using OWASP Dependency-Check for security scanning
                // sh 'mvn dependency-check:check'
            }
            post {
                success {
                    emailext (
                        subject: "Security Scan Successful",
                        body: "The Security Scan stage completed successfully.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
                failure {
                    emailext (
                        subject: "Security Scan Failed",
                        body: "The Security Scan stage failed.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Example of deploying to AWS EC2
                // sh 'scp -i /path/to/key.pem target/app.jar ec2-user@staging-server:/path/to/deploy/'
            }
            post {
                success {
                    emailext (
                        subject: "Deploy to Staging Successful",
                        body: "The Deploy to Staging stage completed successfully.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
                failure {
                    emailext (
                        subject: "Deploy to Staging Failed",
                        body: "The Deploy to Staging stage failed.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Run additional integration tests on staging environment
                // sh 'mvn test -Pstaging'
            }
            post {
                success {
                    emailext (
                        subject: "Integration Tests on Staging Successful",
                        body: "The Integration Tests on Staging stage completed successfully.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
                failure {
                    emailext (
                        subject: "Integration Tests on Staging Failed",
                        body: "The Integration Tests on Staging stage failed.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Example of deploying to production server
                // sh 'scp -i /path/to/key.pem target/app.jar ec2-user@production-server:/path/to/deploy/'
            }
            post {
                success {
                    emailext (
                        subject: "Deploy to Production Successful",
                        body: "The Deploy to Production stage completed successfully.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
                failure {
                    emailext (
                        subject: "Deploy to Production Failed",
                        body: "The Deploy to Production stage failed.",
                        to: "junayedalam.au@gmail.com"
                    )
                }
            }
        }
    }
}
