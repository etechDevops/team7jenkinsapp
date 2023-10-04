pipeline {
    agent {
		label {
			label 'slave1'
		}
	}
    stages {
        stage('version-control') {
            steps {
                checkout scm(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'team7-git-id', url: 'https://github.com/etechDevops/team7jenkinsapp.git']])
            }
        }
        stage('artifactbuild') {
            steps {
                sh 'df -h'
            }
        }
        stage('parallel') {
            parallel {
                stage('unitest') {
                    steps {
                        sh 'lscpu'
                    }
                }
                stage('deploy') {
                    agent {
						label {
							label 'slave2'
						}
                    }
                    steps {
                        echo "we are on pipeline as code module"
                    }
                }
            }
        }
        stage('security_check') {
            steps {
                echo "end of the session"
            }
        }
    }
}
