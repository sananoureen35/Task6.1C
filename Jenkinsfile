pipeline {
    agent any
environment {
        ENV_VARIABLE = 'EnvVar'
    }
    stages {
        stage('Build') {
            steps {
                echo "building the code using a maven build automation tool"
                //sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
            echo "running unit tests to ensure the code functions as expected"
            //sh 'mvn test'
            }
        }
       stage('Code Analysis') {
    steps {
        echo "analyzing the code to ensure it meets the industry standard"
        //sh 'sonar-scanner' using SonarQube
    }
}
        stage('Security Scan') {
            steps {
                echo "Performing security scan to identify any vulnerabilities"
                //sh 'run-security-scan.sh'
            }
            post {
                always {
                          mail to: 'sananoureen35@gmail.com',
                                     subject: "Security Scan Outcome for ${env.JOB_NAME}",
                                     body: "Review the Jenkins console output report from the security scan performed to know the scan result."
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "deploying the application to staging environment"
                //sh './deploy_staging.sh' 
           }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "running integration tests on staging"
                 //sh 'run-integration-tests.sh'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy application to production"
                 //sh './deploy_production.sh' 
           }
        }
    }
    post {
    always {
        mail bcc: '', 
             cc: '', 
             from: '', 
             replyTo: '', 
             subject: "Pipeline execution report for ${env.JOB_NAME}",
             body: "The Pipeline execution has been completed. Please review the Jenkins console output for pipeline execution details.",
             to: "sananoureen35@gmail.com"
        }
    }
}
    