node {
     stage('Clone repository') {
         checkout scm
     }
     stage('Build image') {
         app = docker.build("Gyeongun/flask-example")
         
     }
     stage('Push image') {
         docker.withRegistry('https://54.197.19.111', 'harbor_cred') {
             app.push("${env.BUILD_NUMBER}")
             app.push("latest")
         }
     }
}
