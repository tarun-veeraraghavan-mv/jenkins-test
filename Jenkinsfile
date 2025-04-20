pipeline {
	agent any

  environment {
    dockerHome = tool 'myDocker'
    mavenHome = tool 'myMaven'
    PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
  }

  stages {
    stage("Checkout") {
      steps {
        echo "build"
        echo "$env.BUILD_NUMBER"
        echo "BUILDID - $env.BUILD_ID"
        echo "BUILD URL - $env.BUILD_URL"
      }
    }

    stage("Build") {
      steps {
        sh "npm install"
        sh "node app.js"
      }
    }

    stage("Build docker image") {
      steps {
        echo "Building image..."
        "docker build -t tarun764/node-jenkin:$env.BUILD_TAG"
        script {
          dockerImage = docker.build("tarun764/node-jenkin:${env.BUILD_TAG}")
        }
        echo "New image built..."
      }
    }

    stage("Push docker image") {
      steps {
        script {
          docker.withRegistry('', 'dockerhub') {
            dockerImage.push();
            dockerImage.push('latest');
          }
        }
      }
    }
  } 

  post{
      always{
          echo "====++++always++++===="
      }
      success{
          echo "====++++only when successful++++===="
      }
      failure{
          echo "====++++only when failed++++===="
      }
  }
}