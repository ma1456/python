pipeline {
    agent any
    options { 
        timeout(time: 1, unit: 'HOURS')
    }
    stages {
        stage('Checkout project') {
            steps {
                script {
                    git branch: "master",
                        credentialsId: 'MANOJ_PYTHON',
                        url: 'https://github.com/ma1456/python.git'
                }
            }
        }
        stage('Installing packages') {
            steps {
                script {
                    sh 'pip install -r requirements.txt'
                }
            }
        }
        
        stage('Running Unit tests') {
            steps {
                script {
                    sh 'python3 -m unit test test_test1.py'
                    junit "pyunit.xml"
                }
            }
        }
    }   
}    