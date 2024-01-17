pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/linkonabe/curriculum-app', branch: 'jen')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build') {
      steps {
        sh '''sudo chmod 660 /var/run/docker.sock
&& sudo systemctl restart docker
&& docker build -f curriculum-front/Dockerfile -t fuze365/curriculum-front:latest .
'''
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'fuze365'
        DOCKERHUB_PASSWORD = 'gv1&3Ea9W##onDQAMUG&41CvZ7h1d1'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push fuze365/curriculum-front:latest'
      }
    }

  }
}