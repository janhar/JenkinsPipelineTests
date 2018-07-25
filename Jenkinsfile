def COOL

pipeline {
    agent none
    parameters { booleanParam(name: 'DEBUG_BUILD', defaultValue: true, description: '') }
    stages {
        stage("A") {
            agent {
                label 'master'
            }
            when {
                environment name: 'DEBUG_BUILD', value: "true"
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
