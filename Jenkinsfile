pipeline {
	agent {
    docker {
      image 'tarun764/node-jenkin'
    }
  }

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
        sh "npm run dev"
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