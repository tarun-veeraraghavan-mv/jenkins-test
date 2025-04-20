pipeline {
	agent {
    docker {
      image 'node:18'
    }
  }

  environment {
    dockerHome = tool 'myDocker'
    mavenHome = tool 'myMaven'
    PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
  }

  stages {
    stage("Build") {
      steps {
        echo "build"
        echo "$env.BUILD_NUMBER"
        echo "BUILDID - $env.BUILD_ID"
        echo "BUILD URL - $env.BUILD_URL"
      }
    }

    stage("Test") {
      steps {
        echo "test"
      }
    }

    stage("Intergration test") {
      steps {
        echo "test"
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