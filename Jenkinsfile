pipeline{
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
archiveArtifacts artifacts: '', followSymlinks: false
      }
    }
    stage('Build docker images'){
      steps{
        echo "Building docker images"
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
