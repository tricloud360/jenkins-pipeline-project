pipeline {
    agent any
    
    environment {
        BUILD_REPORT = ""
    }
    
    stages {
        stage('Fetch Git Commit') {
            steps {
                script {
                    def gitCommit = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
                    def gitBranch = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
                    def gitAuthor = sh(returnStdout: true, script: 'git log -1 --pretty=format:"%an"').trim()
                    def commitMessage = sh(returnStdout: true, script: 'git log -1 --pretty=format:"%s"').trim()
                    
                    echo "Git Commit: ${gitCommit}"
                    echo "Git Branch: ${gitBranch}"
                    echo "Commit Author: ${gitAuthor}"
                    echo "Commit Message: ${commitMessage}"
                    
                    env.BUILD_REPORT += """Git Information:
                    Commit: ${gitCommit}
                    Branch: ${gitBranch}
                    Author: ${gitAuthor}
                    Message: ${commitMessage}
                    
                    """
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    def stageName = "Build"
                    def stageDescription = """
                    Description: This stage compiles and packages the code.
                    Tool: Maven
                    
                    Maven is used as the build automation tool. It manages project dependencies,
                    compiles source code, runs tests, and packages the application into a deployable format.
                    
                    Command that would be used: mvn clean package
                    """
                    
                    echo "${stageName}\n${stageDescription}"
                    
                    // Simulating the build process
                    sh 'echo "Building the project with Maven"'
                    // sh 'mvn clean package'
                    
                    env.BUILD_REPORT += "${stageName}: SUCCESS\n${stageDescription}\n\n"
                }
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                script {
                    def stageName = "Unit and Integration Tests"
                    def stageDescription = """
                    Description: This stage runs unit tests and integration tests to ensure code quality and functionality.
                    Tools: JUnit for unit testing, Selenium for integration testing
                    
                    JUnit is used for unit testing individual components, while Selenium is used for 
                    integration testing to ensure different parts of the application work together correctly.
                    
                    Commands that would be used:
                    Unit Tests: mvn test
                    Integration Tests: mvn integration-test
                    """
                    
                    echo "${stageName}\n${stageDescription}"
                    
                    // Simulating the testing process
                    sh 'echo "Running unit tests with JUnit"'
                    sh 'echo "Running integration tests with Selenium"'
                    // sh 'mvn test'
                    // sh 'mvn integration-test'
                    
                    env.BUILD_REPORT += "${stageName}: SUCCESS\n${stageDescription}\n\n"
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                script {
                    def stageName = "Code Analysis"
                    def stageDescription = """
                    Description: This stage analyzes the code to ensure it meets industry standards.
                    Tool: SonarQube
                    
                    SonarQube is used for continuous inspection of code quality. It performs 
                    automatic reviews with static analysis of code to detect bugs, code smells, 
                    and security vulnerabilities.
                    
                    Command that would be used: mvn sonar:sonar
                    """
                    
                    echo "${stageName}\n${stageDescription}"
                    
                    // Simulating the code analysis process
                    sh 'echo "Performing code analysis with SonarQube"'
                    // sh 'mvn sonar:sonar'
                    
                    env.BUILD_REPORT += "${stageName}: SUCCESS\n${stageDescription}\n\n"
                }
            }
        }
        
        stage('Security Scan') {
            steps {
                script {
                    def stageName = "Security Scan"
                    def stageDescription = """
                    Description: This stage performs a security scan to identify vulnerabilities.
                    Tool: OWASP Dependency-Check
                    
                    OWASP Dependency-Check is used to detect publicly disclosed vulnerabilities in 
                    project dependencies. It helps identify and report known vulnerabilities in the project.
                    
                    Command that would be used: mvn org.owasp:dependency-check-maven:check
                    """
                    
                    echo "${stageName}\n${stageDescription}"
                    
                    // Simulating the security scan process
                    sh 'echo "Performing security scan with OWASP Dependency-Check"'
                    // sh 'mvn org.owasp:dependency-check-maven:check'
                    
                    env.BUILD_REPORT += "${stageName}: SUCCESS\n${stageDescription}\n\n"
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                script {
                    def stageName = "Deploy to Staging"
                    def stageDescription = """
                    Description: This stage deploys the application to a staging environment.
                    Tool: AWS CLI
                    
                    AWS CLI is used to deploy the application to an AWS EC2 instance that serves 
                    as our staging environment. This allows for testing in a production-like setting.
                    
                    Command that would be used: aws ec2 run-instances --image-id ami-xxxxxxxx --instance-type t2.micro --key-name MyKeyPair
                    """
                    
                    echo "${stageName}\n${stageDescription}"
                    
                    // Simulating the deployment to staging
                    sh 'echo "Deploying to AWS EC2 staging instance"'
                    // sh 'aws ec2 run-instances --image-id ami-xxxxxxxx --instance-type t2.micro --key-name MyKeyPair'
                    
                    env.BUILD_REPORT += "${stageName}: SUCCESS\n${stageDescription}\n\n"
                }
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                script {
                    def stageName = "Integration Tests on Staging"
                    def stageDescription = """
                    Description: This stage runs integration tests in the staging environment.
                    Tool: Postman/Newman
                    
                    Postman/Newman is used for running API tests in the staging environment to ensure 
                    the application functions correctly in a production-like setting.
                    
                    Command that would be used: newman run postman_collection.json -e staging_environment.json
                    """
                    
                    echo "${stageName}\n${stageDescription}"
                    
                    // Simulating integration tests on staging
                    sh 'echo "Running integration tests on staging with Postman/Newman"'
                    // sh 'newman run postman_collection.json -e staging_environment.json'
                    
                    env.BUILD_REPORT += "${stageName}: SUCCESS\n${stageDescription}\n\n"
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                script {
                    def stageName = "Deploy to Production"
                    def stageDescription = """
                    Description: This stage deploys the application to the production environment.
                    Tool: AWS CLI
                    
                    AWS CLI is used again, this time to deploy the tested and verified application 
                    to an AWS EC2 instance that serves as our production environment.
                    
                    Command that would be used: aws ec2 run-instances --image-id ami-xxxxxxxx --instance-type t2.micro --key-name MyKeyPair
                    """
                    
                    echo "${stageName}\n${stageDescription}"
                    
                    // Simulating the deployment to production
                    sh 'echo "Deploying to AWS EC2 production instance"'
                    // sh 'aws ec2 run-instances --image-id ami-xxxxxxxx --instance-type t2.micro --key-name MyKeyPair'
                    
                    env.BUILD_REPORT += "${stageName}: SUCCESS\n${stageDescription}\n\n"
                }
            }
        }
    }
    
    post {
        always {
            script {
                def buildStatus = currentBuild.result ?: 'SUCCESS'
                def subject = "Build ${env.BUILD_NUMBER} - ${buildStatus}"
                def body = """
                Jenkins Build ${env.BUILD_NUMBER} - ${buildStatus}
                
                Job: ${env.JOB_NAME}
                Build Number: ${env.BUILD_NUMBER}
                Build URL: ${env.BUILD_URL}
                
                Comprehensive Build Report:
                
                ${env.BUILD_REPORT}
                """
                
                emailext subject: subject,
                         body: body,
                         to: 'tricloud360@gmail.com',
                         attachLog: true
            }
        }
    }
}

// End of Jenkinsfile testing ssd