node {
environment { 
        repository = "guhan73/flask-example"  //docker hub id와 repository 이름
        DOCKERHUB_CREDENTIALS = credentials('sue-dockerhub') // jenkins에 등록해 놓은 docker hub credentials 이름
        dockerImage = '' 
  }
     
     stage('Clone repository') {
         checkout scm
     }
     stage('Build image') {
         app = docker.build("gyeongun/flask-example")
         
     }
     stage('Push image') {
         docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
             app.push("$repository.${BUILD_NUMBER}")
             app.push("latest")
         }
     }
}

stage('Build image') {
  app = docker.build("gyeongun/flask-example")
}

stage('Push image') {
  docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') 
  {
     app.push("${env.BUILD_NUMBER}")
     app.push("${"guhan73/flask-example":BUILD_NUMBER}")
     app.push("latest")
  }
}
