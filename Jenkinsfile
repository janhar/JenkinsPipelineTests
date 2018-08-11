def failed=false
pipeline {
    agent none
    options {
        skipDefaultCheckout true
      }
    stages {
        stage("A") {
            agent {
                label 'master'
            }
            steps {
                script {
                    try {
                        echo 'A'
                        sh 'exit -1;'
                    } catch(exc) {
                        failed=true
                    }
                }    
            }
        }
        stage("B") {
            agent {
                label 'master'
            }
            steps {
                script {
                    if(failed) {
                        currentBuild.currentResult='FAILURE'
                        echo 'B'
                    }
                }
            }
        }
        stage("C") {
            agent {
                label 'master'
            }
            steps {
                echo 'C'
            }
        }
    }
}
