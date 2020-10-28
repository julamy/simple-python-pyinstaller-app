pipeline {
    agent none 
    stages {
        stage('Initialize'){
          def dockerHome = tool 'mydocker'
          env.PATH = "${dockerHome}/bin:${env.PATH}"
        }
        stage('Build') { 
            agent {
                docker {
                    image 'python:2-alpine' 
                }
            }
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py' 
                stash(name: 'compiled-results', includes: 'sources/*.py*') 
            }
        }
    }
}
