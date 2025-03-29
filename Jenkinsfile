pipeline {
    agent { label 'linux'}
    tools {
        maven 'Maven-3.9.9'
    }
    stages {
        stage('Source') {
            steps {
                sh 'mvn --version'
                sh 'git --version'
                git branch: 'master', url: 'https://github.com/vikaskaushik3/run_pipeline_on_ssh_agent.git'
            }
        }

        stage('Clean') {
            steps {
                dir("${env.WORKSPACE}/Ch04/04_02-ssh-agent"){
                    sh 'mvn clean'
                }
            }
        }

        stage('Test'){
            steps {
                dir("${env.WORKSPACE}/Ch04/04_02-ssh-agent"){
                    sh 'mvn test'
                }
            }
        }

        stage('Package'){
            steps {
                dir("${env.WORKSPACE}/Ch04/04_02-ssh-agent"){
                    sh 'mvn package -DskipTests'
                }
            }
        }

    }

}