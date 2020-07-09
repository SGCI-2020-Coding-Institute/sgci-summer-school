# Prerequisites:
1. Make sure you have git and python. Install if necessary. 
2. Install flask: https://flask.palletsprojects.com/en/1.1.x/installation/
3. Install docker: https://docs.docker.com/get-docker/
4. Use Docker to install Kubernetes: https://docs.docker.com/get-started/kube-deploy/

# Make a simple Flask application
1. Check out the sample code:
   `git clone https://github.com/marpierc/sgci-summer-school.git`

2. Change to the project dictory:
   `cd sgci-summer-school`
      
3. Run the flask demo directly from the command line:
   `python demo.py`

4. Point your browser to http://localhost:5001 to confirm that your server is now running.

# Make and run a Docker container for your flask application
Before proceeding, work through the instructions at https://docs.docker.com/get-started/ (all three parts) to verify that you have docker installed correctly. 

Execute all of these steps in the sgci-summer-school directory.

1. Make the container:
   `docker build --tag flask-demo:0.1 .`

2. Optionally, push your container to DockerHub, replacing <YOUR_DOCKERHUB_REPO> with the name of the hub that you created in step 3 of the Docker intro (https://docs.docker.com/get-started/part3/).

   `docker tag flask-demo:1.0 <YOUR_DOCKERHUB_REPO>/flask-demo:1.0`
   `docker push <YOUR_DOCKERHUB_REPO>/flask-demo:1.0`

3. 


   