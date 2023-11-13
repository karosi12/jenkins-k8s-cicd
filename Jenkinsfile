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
        environment {
            AWS_ACCESS_KEY_ID = credentials('jenkins_aws_access_key_id')
            AWS_SECRET_ACCESS_KEY = credentials('jenkins_aws_secret_key_id')
        }
        steps {
            script {
                echo 'Deploying docker image...'
                sh 'kubectl create deployment nginx-deployment --image=nginx'
            }
      }
    }
  }
}