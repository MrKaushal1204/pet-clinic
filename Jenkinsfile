pipeline{
  environment{
    registry = "mrkaushal1204/pet-clinic"
    registryCredential = "docker_hub_d3athstalker"
    dockerImage =''
  }
  agent any
  stages{
    stage('Build'){
      steps{
        echo "Building project"
        sh './mvnw package'
      }
    }
    stage('Archive'){
      steps{
        echo "Archiving project"
        archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
      }
    }
    stage('Build docker images'){
      steps{
        echo "Building docker images"
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER" 
        }
      }
    }
    stage('Push docker image'){
      steps{
        echo "Pushing docker image"
      }
    }
    stage('Deploy to Dev'){
      steps{
        echo "Deploying to dev environment"
      }
    }
  }
}
