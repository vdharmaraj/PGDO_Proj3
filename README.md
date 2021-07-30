# PGDO_Proj3
<h1>Project: <i>Build a Docker Jenkins Pipeline to Implement CI/CD Workflow</i> </h1> </br>


<h2>Objective:</h2> Demonstrate the continuous integration and delivery by building a Docker Jenkins Pipeline.  </br>

<h2>Solution build should demonstrate below capabilities: </h2> </br>
•	Availability of the application and its versions in the GitHub </br>
•	Track their versions every time a code is committed to the repository  </br>
•	Create a Docker Jenkins Pipeline that will create a Docker image from the Dockerfile and host it on Docker Hub  </br>
•	It should also pull the Docker image and run it as a Docker container  </br>
•	Build the Docker Jenkins Pipeline to demonstrate the continuous integration and continuous delivery workflow  </br>

<h2>Project goal</h2> is to deliver the software product frequently to the production with high-end quality.  </br>


<h2>Tools required:</h2> Docker, Docker Hub, GitHub, Git, Linux (Ubuntu), Jenkins  </br>

<h2>Project Expected Result:</h2>
Jenkins pipeline with stages as shown below, demonstrating the Springboot application build and deployment process automated with Docker and Jenkins with 'Pipeline as a Code' approach</br>
[pipeline output image](https://github.com/vdharmaraj/PGDO_Proj3/blob/681fdb351bdec410700e161758e2cacc4ccc9bed/Documentation/Jenkins_pipeline_result.JPG?raw=true)

<h2>Project Documentation</h2>
Click [here](https://github.com/vdharmaraj/PGDO_Proj3/blob/681fdb351bdec410700e161758e2cacc4ccc9bed/Documentation/PG%20DO%20-%20DevOps%20Certification%20Training_Project-3_Vignesh_Dharmaraj.pdf) to access the project documentation I have created to submit for my DevOps PG certification program requirements   

<h2>Solution overview:</h2> 
1) On a Linux (ubantu) machine, we are installing and configuring jenkins server.</br>
2) In the jenkins server we are creating the pipeline based project (with the Jenkinsfile available in this repo as source)</br>
3) First Stage in the pipeline is to pull the latest springboot application (index.html) changes from SCM (Git-Hub) 
4) Next stage in the pipeline is to create a build using maven tool and the pom.xml file available in the code repository</br>
5) Next stage in the pipeline will create docker image based on the standard java container with our jar executable created as a result of the build process in the previous step (Dockerfile available in the repo is responsible to create this image)</br>
6) Next stage in the pipleline will push the lastest doker image created in the previous stage to the Docker Hub (remote image repository)</br>
7) Next stage in the pipeline will remove any existing containers of our application</br>
8) Next stage in the pipeline will start new container with the latest image (including our latest changes of springboot application) pulled from docker hub</br>
9) Next stage in the pipeline will remove any old images in our linux machine</br>

<h2>Mandatory changes to be made in Jenkinsfile when you want to use this project</h2>

1. Its mandatory to change the Docker Hub Account ID after this Repo is forked/cloned by an other person</br>
    def dockerhubaccountid = "vikidvg"</br>
    

2. To push image to remote repository , in your jenkins server you have to create the global credentials similar to the 'dockerHub' (credential ID)</br>
  
	     docker.withRegistry('', 'dockerHub') {
             dockerImage.push("${env.BUILD_NUMBER}")
             dockerImage.push("latest")
            }
	    
3. Update your Forked/cloned Repo URL in the stage('Clone Repo') 
