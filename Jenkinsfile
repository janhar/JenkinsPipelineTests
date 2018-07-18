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
                sh './script.sh'
		sh '''
		  echo 'First line'
		  echo 'Second line'
                '''
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
                input 'del'
                echo 'B'
                cleanWs()
                script {
                    if(COOL == null) {
                        COOL = 'super cool B'
                    }
                }
                input 'check'

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
