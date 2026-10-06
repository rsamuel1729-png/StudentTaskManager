pipeline {
 agent any
 stages {
  stage('Checkout'){steps{checkout scm}}
  stage('Build'){steps{bat 'docker build -t student-task-manager .'}}
  stage('Deploy'){steps{
   bat 'docker stop student-task-app 2>nul || echo Container not running'
   bat 'docker rm student-task-app 2>nul || echo Container not found'
   bat 'docker run -d -p 3000:80 --name student-task-app student-task-manager'
  }}
 }
}