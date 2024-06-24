pipeline {
  agent any

  options {
    timeout(time: 2, unit: 'MINUTES')
  }

  environment {
        DOCKER_IMAGE = 'jenkinsfile_pin'
        DOCKER_USER = 'farguello1995'
        DOCKER_REPO = 'nombre_de_tu_repositorio'
        DOCKER_TAG = 'v1'
        DOCKER_PASS = credentials('docker-pass-cred')
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
        sh "docker images"
      }
    }
    stage('Login in dockerhub'){
      steps {
        echo "${DOCKER_USER}"
        sh "docker login -u ${DOCKER_USER} -p ${DOCKER_PASS}"
        
      }
    }
    stage("Push registry") {
      steps{
        sh "docker tag ${DOCKER_USER}/${DOCKER_IMAGE}:${DOCKER_TAG} ${DOCKER_USER}/${DOCKER_IMAGE}:v2"
        sh "docker push ${DOCKER_USER}/${DOCKER_IMAGE}:v2"
      }
    }
   }
}


    
  

