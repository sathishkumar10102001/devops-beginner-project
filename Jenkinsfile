pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/sathishkumar10102001/devops-beginner-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t beginner-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f beginner-container || true
                docker run -d --name beginner-container -p 8082:80 beginner-app
                '''
            }
        }
    }
}

