pipeline {
    agent { label'JDK8' }
    options { 
        timeout(time: 1, unit: 'HOURS')
    }
    stages {
        stage('Checkout project') {
            steps {
                script {
                    git branch: "master",
                        credentialsId: 'my-credentials',
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
                    sh 'python -m unit test test_test1.py'
                    junit "pyunit.xml"
                }
            }
        }
    }   
}    