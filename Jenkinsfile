node ('ubuntuagent1'){  
    def app
    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
       checkout scm
    }  
    
     stage('SAST') {
        /* Let's make sure we have the repository cloned to our workspace */
       build 'synktest1'
    }  
    
    stage('Build-and-Tag') {
    /* This builds the actual image; synonymous to
         * docker build on the command line */
        app = docker.build("sksksk/snap300:v1")
    }
    stage('Post-to-dockerhub') {
    
     docker.withRegistry('https://registry.hub.docker.com', 'dockercred') {
            app.push("v1")
        			}
         }
    
    stage('imagescanner') {
        /* Let's make sure we have the repository cloned to our workspace */
       build 'aquamicroscanner'
  
    stage('Pull-image-server') {
    
         sh "docker-compose down"
         sh "docker-compose up -d"	
      }
        
        stage('DAST'){
         build 'aquamicroscanner'    
        }

}
