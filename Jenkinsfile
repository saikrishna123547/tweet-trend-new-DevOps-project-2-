pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.5/bin:$PATH"
}
    stages {
        stage("build") {
            steps {
               echo "---------------Build started----------------"
               sh 'mvn clean deploy -Dmaven.test.skip=true'
               echo "---------------Build completed----------------"
            }
        }
        stage("test") {
            steps {
               echo "---------------test cases started----------------"
               sh 'mvn surefire-report:report'
               echo "---------------test cases completed----------------"
            }
        }
        stage("SonarQube analysis") {
        environment {
            scannerHome = tool 'valaxy-sonar-scanner'
        }
            steps {
                withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
                sh "${scannerHome}/bin/sonar-scanner"
                }
            }
            
        }
    }
}
