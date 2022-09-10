node {
    def app

    stage('Clone repository') {
        /*make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* synonymous to
         * docker build on the command line
         *between the "" insert docker hub username followed by "/" 
         *and the name of the repo you want to create on dokerhub*/

        app = docker.build "fravaccaro/first-node-image"
    }

    stage('Test image') {
        /* emulating a test */

        app.inside {
            sh 'echo "Tests passed"'
       }
    }

    stage('Push image') {
        /* push image built on docker hub. 
        *  the variable docker-hub-credential contains the credential that are previous set in the Jenkins/credentials*/
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
       }
    
    }
}