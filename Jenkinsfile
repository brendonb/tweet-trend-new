pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    environment {
        PATH ="/opt/apache-maven-3.9.9/bin:$PATH"
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean deploy'
                git branch: 'main', url: 'https://github.com/brendonb/tweet-trend-new.git'
            }
        }
    }

    stage("SonarQube analysis") {

    environment{
        scannerHome = tool 'sonar-scanner'
        }
        steps{
            withSonarQubeEnv('sonarqube-server') {
                 sh "${scannerHome}/bin/sonar-scanner"
              }
        }
        
          
      }
}