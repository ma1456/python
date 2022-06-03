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
        stage('Static Code Checking') {
            steps {
                script {
                    sh 'find . -name \\*.py | xargs pylint -f parseable | tee pylint.log'
                }
            }
        }
        stage('Running Unit tests') {
            steps {
                script {
                    sh 'pytest --with-xunit --xunit-file=pyunit.xml --cover-xml --cover-xml-file=cov.xml tests/*.py || true'
                    junit "pyunit.xml"
                }
            }
        }
    }   
}    