node {
    def app

    stage('Clone repository') {
        /*make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* synonymous to
         * docker build on the command line */

        app = docker.build("First-Node-Project")
    }

    stage('Test image') {
        /* emulating a test */

        app.inside {
            sh 'echo "Tests passed"'
       }
    }

    stage('Push image') {
        /* push image built on docker hub. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
       }
    
}