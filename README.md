# Prerequisites:
1. Make sure you have git and python. Install if necessary. 
2. Install flask: https://flask.palletsprojects.com/en/1.1.x/installation/
3. Install docker: https://docs.docker.com/get-docker/
4. Use Docker to install Kubernetes: https://docs.docker.com/get-started/orchestration/

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

2. Run your container:
   `docker run -d -p5000:5001 --name junk-test flask-demo:0.1`

3. Point your browser to http://localhost:5000 to verify that the server is running. 

4. Optionally, push your container to DockerHub, replacing <YOUR_DOCKERHUB_REPO> with the name of the hub that you created in step 3 of the Docker intro (https://docs.docker.com/get-started/part3/).

   ```
   docker tag flask-demo:1.0 <YOUR_DOCKERHUB_REPO>/flask-demo:1.0
   docker push <YOUR_DOCKERHUB_REPO>/flask-demo:1.0
   ```

Now anyone who wants to use your application can just download it from DockerHub and run it in their own local Docker environment.

5. Stop and remove your container instance:
   `docker rm --force junk-test`

While we can run services in Docker, container orchestration engines like Kubernetes are much more powerful ways of doing this.

# Use Kubernetes to run the container with your flask application
Before proceeding, make sure that Kubernetes is installed by following the instructions at https://docs.docker.com/get-started/orchestration/.  Skip the instructions for installing Swarm.  Kubernetes should be running on your system. 

1. Deploy you service into Kubernetes: `kubectl apply -f demo-pod.yaml`

2. Confirm that the service is running by pointing your browser to http://localhost:30001

3. Stop your service with `kubectl delete -f demo-pod.yaml`


If you update your Flask code, you can update the service you are running in Kubernetes to use the new code as follows:

1. Remake the docker container: `docker build --tag flask-demo:0.1 .`

2. Update Kubernetes: `kubectl rollout restart deployment/flask-demo`

Make a trivial change to your flask app and confirm that it returns different responses before and after the restart.








   