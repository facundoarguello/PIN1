pipeline {
  agent {
        docker {
            image 'docker:19.03.12' // Imagen Docker-in-Docker (dind)
            args '--privileged' // Necesario para Docker-in-Docker
        }
    }

  options {
    timeout(time: 2, unit: 'MINUTES')
  }

  environment {
        DOCKER_IMAGE = 'jenkinsfile_pin'
        DOCKER_USER = 'farguello1995'
        DOCKER_REPO = 'nombre_de_tu_repositorio'
        DOCKER_TAG = 'v1'
  }
   stages {
   stage('pull image') {
      steps{
          sh """
          docker pull ${DOCKER_USER}/${DOCKER_IMAGE}:${DOCKER_TAG}
             """ 
        }
    }
  
  
    stage('Run tests') {
      steps {
        sh "docker IMAGES"
      }
    }
   }
}


    
  

