def dockerImageTag = "suguksops/projectimages:new-${BUILD_NUMBER}"

node {
   
    stage('Checkout') {
        
        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/naturekey/docker.git']])
       
    }
    stage('DockerImageBuild') {
        def dockerImage = docker.build(dockerImageTag)
      
    }
    stage('Push to DockerHUB') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerHUB') {
        def dockerImage = docker.image(dockerImageTag)
        dockerImage.push()
     }
    }
}
