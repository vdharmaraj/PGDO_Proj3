# PGDO_Proj3
<h1>Build a Docker Jenkins Pipeline to Implement CI/CD Workflow </h1> </br>


<h2>Objective:</h2> Demonstrate the continuous integration and delivery by building a Docker Jenkins Pipeline.  </br>

<h2>Solution build should demonstrate below capabilities: </h2> </br>
•	Availability of the application and its versions in the GitHub </br>
•	Track their versions every time a code is committed to the repository  </br>
•	Create a Docker Jenkins Pipeline that will create a Docker image from the Dockerfile and host it on Docker Hub  </br>
•	It should also pull the Docker image and run it as a Docker container  </br>
•	Build the Docker Jenkins Pipeline to demonstrate the continuous integration and continuous delivery workflow  </br>

<h2>Project goal</h2> is to deliver the software product frequently to the production with high-end quality.  </br>


<h2>Tools required:</h2> Docker, Docker Hub, GitHub, Git, Linux (Ubuntu), Jenkins  </br>

<h2>Mandatory changes to be made in Jenkinsfile when you want to use this project</h2>
//Its mandatory to change the Docker Hub Account ID after this Repo is forked by an other person </br>
    def dockerhubaccountid = "vikidvg" </br>
    
//To push image to remote repository , in your jenkins server you have to create the global credentials similar to the 'dockerHub' (credential ID)</br>
  
	     docker.withRegistry('', 'dockerHub') {
             dockerImage.push("${env.BUILD_NUMBER}")
             dockerImage.push("latest")
            }
