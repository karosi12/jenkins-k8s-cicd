def gv

pipeline {
  agent any
  stages{
    stage("test"){
      steps{
        script{
          echo 'Running test - 🔍'
        }
      }
    }
    stage("build"){
      steps{
        script{
          echo 'Building docker image'
        }
      }
    }
    stage('deploy') {
      steps {
        environment {
            AWS_ACCESS_KEY_ID = credentials('jenkins_aws_access_key_id')
            AWS_SECRET_KEY_ID = credentials('jenkins_aws_secret_key_id')
        }
        script {
            echo 'Deploying docker image...'
            sh 'kubectl create deployment nginx-deployment --image=nginx'
        }
      }
    }
  }
}