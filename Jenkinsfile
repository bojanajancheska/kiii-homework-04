node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("bojanajancheska/kiii-homework-04")
    }
    stage('Push image') {   
       steps {
                script {
                    // right parameter is jenkins credentials
                   docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                       app.push("latest")  
                   }
                }
            }
    }
}
