first project with jenkins and docker

I created a simple Node.js app and dockerized it

STEPS:

-Run a container with Jenkins and install Docker as well in the same container(I use an imaged I previus created with what I needed): docker run -d -p 8080:8080 -p 50000:50000 -v /var/run/docker.sock:/var/run/docker.sock -v jenkins_home:/var/jenkins_home --restart=on-failure fravaccaro94/jenkins
-Install Docker and Docker plugin in Jenkins/plugin
-Insert Docker Credentials
-Create a new pipeline project and insert the Git repository URL in "URL di Deposito" under SCM sub-ection in Pipeline section. In Definition, under Pipeline section set "Pipeline script from SCM". Remember to ser the right branch (*/master).
- in Build triggers set Github hook trigger
-build the project