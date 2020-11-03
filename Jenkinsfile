pipeline {

    agent any

    stages {

        stage("Install") {

            steps{

                sh 'npm install'
            }
        }

        stage("Test") {

            steps{
                
                withSonarQubeEnv('sonarqube'){

                    sh "C:\scanner\sonar-scanner-4.4.0.2170\bin\sonar-scanner"
          
                    }

                    timeout(time: 10, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
            }
                
            }

        }

        stage("Build") {

            steps{
                sh 'npm run-script build'
            }
        }
    }
}