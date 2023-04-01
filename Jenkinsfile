pipeline{
    agent{
        label 'docker'
    }
    stages{
        stage('checkout git'){
            steps{
                dir('vector-role'){
                    git branch: 'main', credentialsId: 'f18be4bd-34ae-4d01-ce2f-7ea1c7caf1d1', url: 'git@github.com:Dimi-link/vector-role.git'
                }
            }
        }
        stage('install dependencies'){
            steps{
                dir('vector-role'){
                    sh 'pip3 install -r requirements.txt'
                }
            }
        }
        stage('run molecule'){
            steps{
                dir('vector-role'){
                    sh 'molecule test'
                }
            }
        }
    }
}