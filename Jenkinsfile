def COOL

pipeline {
    agent none
    options {
        skipDefaultCheckout true
      }
    //parameters { booleanParam(name: 'DEBUG_BUILD', defaultValue: true, description: '') }
    stages {
        stage("A") {
            agent {
                label 'mac'
            }
            /*when {
                environment name: 'DEBUG_BUILD', value: "true"
            }*/
            steps {
                showDirectory()
                //sh './script.sh'
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
                stage('Test On Windows') {
                    agent {
                        label {
                            label 'mac'
                            //customWorkspace 'windows'
                        }
                    }
                    steps {
                        showDirectory()
                        sh 'touch 1.txt'
                    }
                }
                stage('Test On Linux') {
                    agent {
                        label {
                            label 'mac'
                            //customWorkspace 'linux'
                        }
                    }
                    steps {
                        showDirectory()
                        sh 'touch 2.txt'
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
