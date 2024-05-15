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
            /* post {
                always {
                          mail to: 'sananoureen35@gmail.com',
                                     subject: "Unit and integration Outcome for ${env.JOB_NAME}",
                                     body: "Review the Jenkins console output report at ${env.BUILD_URL} from the tests performed to know the result, Status: ${currentBuild.result}."                    
                }
            }*/
            post {
                always {
                    script {
                        // Send email notification
                        def log = currentBuild.rawBuild.getLog(100).join('\n')
                        emailext(
                            to: 'developer@example.com',
                            subject: "Security Scan: ${currentBuild.currentResult}",
                            body: "Build Status: ${currentBuild.currentResult}\n\nLogs:\n${log}"
                        )
                    }
                }
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
                                     body: "Review the Jenkins console output report at ${env.BUILD_URL} from the security scan performed to know the scan result Status: ${currentBuild.result}."
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
}
    