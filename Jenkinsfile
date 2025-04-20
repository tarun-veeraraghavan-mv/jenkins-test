// pipeline {
// 	agent any

//   environment {
//     dockerHome = tool 'myDocker'
//     mavenHome = tool 'myMaven'
//     PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
//   }

//   stages {
//     stage("Checkout") {
//       steps {
//         echo "build"
//         echo "$env.BUILD_NUMBER"
//         echo "BUILDID - $env.BUILD_ID"
//         echo "BUILD URL - $env.BUILD_URL"
//       }
//     }

//     stage("Build") {
//       steps {
//         sh "npm install"
//         // sh "node app.js"
//       }
//     }

//     stage("Build docker image") {
//       steps {
//         echo "Building image..."
//         "docker build -t tarun764/node-jenkin:$env.BUILD_TAG"
//         script {
//           dockerImage = docker.build("tarun764/node-jenkin:${env.BUILD_TAG}")
//         }
//         echo "New image built..."
//       }
//     }

//     stage("Push docker image") {
//       steps {
//         script {
//           docker.withRegistry('', 'dockerhub') {
//             dockerImage.push();
//             dockerImage.push('latest');
//           }
//         }
//       }
//     }
//   } 

//   post{
//       always{
//           echo "====++++always++++===="
//       }
//       success{
//           echo "====++++only when successful++++===="
//       }
//       failure{
//           echo "====++++only when failed++++===="
//       }
//   }
// }

pipeline {
    agent any

    environment {
        dockerImage = "tarun764/node-jenkin"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out code"
                git 'https://github.com/tarun-veeraraghavan-mv/jenkins-test'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image with the tag based on the build number
                    sh "docker build -t ${dockerImage}:${env.BUILD_TAG} ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Push the Docker image to Docker Hub (if required)
                    sh "docker push ${dockerImage}:${env.BUILD_TAG}"
                }
            }
        }
    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only on success'
        }
        failure {
            echo 'This will run only on failure'
        }
    }
}
