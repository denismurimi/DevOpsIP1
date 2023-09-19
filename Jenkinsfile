pipeline {
  agent any
  tools {
    nodejs 'Nodejs'
  }
  stages {
    stage('Clone Repo') {
      steps {
        echo 'Cloning Repository'
        git 'https://github.com/denismurimi/DevOpsIP1.git'
      }
    }
    stage('Install Dependencies') {
      steps {
        echo 'Installing dependencies'
        sh 'npm install'
      }
    }
    stage('Run Tests') {
      steps {
        echo 'Running tests stage'
        sh 'npm test'
      }
    }
    stage('Build') {
      steps {
        echo 'Building App'
        sh 'npm run build'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying app'
        sh 'npm run deploy'
      }
    }
    stage('Cleanup') {
      steps {
        echo 'Cleaning up'
        sh 'rm -rf temp-folder'
      }
    }
  }
      post {
        success {
            script {
                slackSend(channel: "jenkins", message: "pipeline-slack passed successfully")
            }
        }
    }
}