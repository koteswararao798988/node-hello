# Node APPS DEPLOYER!

Simple node.js app that servers "Hello APPS DEPLOYER!"

Great for testing simple deployments to the cloud

## To host node.js application in docker container with the help of Dockerfile

# Working Process
-->First launch brand new EC2 instance
-->Next install docker and setup the docker with commands
   "sudo yum -y install docker"
   "sudo systemctl start docker"
   "sudo systemctl enable docker"
   "sudo chmod 666 /var/run/docker.sock"
-->Next install GIT tool to clone the node.js application code from the remote platform(Github)
   "sudo yum -y install git"
   "git clone URL link of the node.js application repository"
-->Next write the Docker file with vi/vim edit mode
   "sudo vi Dockerfile"
-->Write the Dockerfile with Instructions as 
# Use an official Node.js runtime as a base image
FROM node:14

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the application files to the working directory
COPY . .

# Expose the port that your app will run on
EXPOSE 3000

# Command to run your application
CMD ["npm", "start"]

-->Next build the image from the Dockerfile through its instructions with the command
  "docker build -t app(image name) .(path of the Dockerfile)"
-->Next run the container from the created image with the help of command as
   "docker run -dt --name web -p 3000:3000 app"
-->Next copy the public ip of the running or existing EC2 instance and browse it along with port 3000.   
