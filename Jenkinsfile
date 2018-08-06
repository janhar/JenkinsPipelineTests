def COOL

pipeline {
    agent none
    options {
        skipDefaultCheckout true
      }
    //parameters { booleanParam(name: 'DEBUG_BUILD', defaultValue: true, description: '') }
    stages {
        agent {
            label 'mac'
        }
        stage("A") {
            /*when {
                environment name: 'DEBUG_BUILD', value: "true"
            }*/
            steps {
                showDirectory()
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
                label 'mac'
                customWorkspace 'lol'
            }
            steps {
                showDirectory()
                //cleanWs()
                script {
                    if(COOL == null) {
                        COOL = 'super cool B'
                    }
                }

                echo "${COOL}"
            }
        }
        stage('Run Tests') {
            parallel {
                agent {
                    label 'mac'
                }
                stage('Test On Windows') {
                    steps {
                        showDirectory()
                    }
                }
                agent {
                    label 'mac'
                }
                stage('Test On Linux') {
                    steps {
                        showDirectory()
                    }
                }
            }
        }
        stage("C") {
            agent {
                label 'mac'
            }
            steps {
                showDirectory()
            }
        }
    }
}

void showDirectory() {
    sh 'pwd'
}
