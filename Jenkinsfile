pipeline {
	agent any

  stages {
    stage("Build") {
      steps {
        echo "build"
        echo "test"
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