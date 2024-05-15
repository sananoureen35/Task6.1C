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
            echo "running unit tests using maven JUnit to ensure the code functions as expected"
            //sh 'mvn test'
            }
        }
       stage('Code Analysis') {
    steps {
        echo "analyzing the code using SonarQube to ensure it meets the industry standard"
        //sh 'sonar-scanner' 
    }
}
        stage('Security Scan') {
            steps {
                echo "Performing security scan using OWASP ZAP or Fortify to identify any vulnerabilities"
                //The OWASP ZAP or Fortify commands are called here
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
                echo "deploying the application to staging environment using Jenkins SSH Plugin"
                //sh './deploy_staging.sh' 
           }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "running integration tests on staging using Selenium"
                 //Selenium commands are called here
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy application to production using Jenkins SSH Plugin"
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
    