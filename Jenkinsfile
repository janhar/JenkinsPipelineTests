def COOL

pipeline {
    agent none
    stages {
        stage("A") {
            agent {
                label 'master'
            }
            steps {
                echo 'A'
                
                script {
                    COOL = 'really cool! A'
                }
            }
        }
        stage("B") {
            agent {
                label 'master'
            }
            steps {
                echo 'B'
                script {
                    if(COOL == null) {
                        COOL = 'super cool B'
                    }
                }
                echo "${COOL}"
            }
        }
        stage("C") {
            agent {
                label 'master'
            }
            steps {
                sh 'printenv'
            }
        }
    }
}