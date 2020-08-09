pipeline{
  environment{
    registry = "d3athstalker/petclinic"
    registryCredential = "docker_hub_d3athstalker"
    dockerImage = ''
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
    stage('Build docker image'){
      steps{
        echo "Building docker image"
        script{
          dockerImage = docker.build registry + ":$BUILD_NUMBER" 
        }
      }
    }
    stage('Push docker image'){
      steps{
        echo "Pushing docker image"
        script{
          docker.withRegistry('',registryCredential) {
            dockerImage.push()
            dockerImage.push('latest')
          }
        }
      }      
    }
    stage('Deploy to Dev'){
      steps{
        echo "Deploying to dev environment"
        sh 'docker run -d --name=petclinic -p 8081:8080 d3athstalker/petclinic'
      }
    }
  }
}
