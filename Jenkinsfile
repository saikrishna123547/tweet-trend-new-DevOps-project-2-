pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    
    stages {
        stage("clone code from git") {
            steps {
                git branch: 'main', url: 'https://github.com/saikrishna123547/tweet-trend-new-DevOps-project-2-.git'
            }
        }
    }
}