

#### I want to build a Local Large Language Model (LLM) and learn about it in the process. The GitHub repository you shared provides a starting point for learning applied generative AI fundamentals.

Let's break down the steps to guide you through this process:

Step 1: Prerequisites
To ensure a smooth learning experience, let's cover the prerequisites:
1. Python Programming
Familiarize yourself with Python 3.x (latest version recommended)
Review basic syntax, data structures (lists, dictionaries, etc.), and control structures (if-else, loops, etc.)
Practice writing Python scripts and functions
2. Basic Machine Learning Concepts
Understand the fundamentals of machine learning, including:
Supervised and unsupervised learning
Regression, classification, and clustering
Model evaluation metrics (accuracy, precision, recall, F1-score, etc.)
Basic neural network concepts (layers, activation functions, etc.)
3. Install Required Libraries and Tools
Install Python 3.x (if you haven't already)
Install the following libraries using pip:
PyTorch (torch)
Transformers (transformers)
Hugging Face's Accelerate (accelerate)
Other dependencies listed in the repository's requirements.txt file
4. Set Up Your Development Environment
Choose a code editor or IDE (Integrated Development Environment) like PyCharm, VSCode, or Jupyter Notebooks



# Step 1: Run the Ollama and OpenWebUI Containers

To run the Ollama container, use this command in the terminal:

```
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
Here’s what each part of the command does:
```

This is a Docker command that runs a container in detached mode (-d) with specific settings. Let's break it down:
docker run: This is the command to create and start a new Docker container.

-d: Run the container in detached mode, meaning it runs in the background and doesn't occupy the terminal.

-v ollama:/root/.ollama: This flag mounts a volume from the host machine to the container. Here's what it does:

ollama: This is the name of the volume on the host machine.

/root/.ollama: This is the path inside the container where the volume will be mounted.

-p 11434:11434: This flag maps a port from the host machine to the container. Here's what it does:
11434: This is the port number on the host machine.
11434: This is the port number inside the container.

--name ollama: This flag sets the name of the container to "ollama".
ollama/ollama: This is the Docker image to use for the container. It's pulling the image from Docker Hub with the name "ollama/ollama".

Now, let's guide you through understanding this command:
Docker volumes: Volumes allow you to persist data even after the container is deleted. In this case, the volume "ollama" is mounted to "/root/.ollama" inside the container.

Port mapping: Port mapping allows you to access the container's ports from the host machine. In this case, port 11434 on the host machine is mapped to port 11434 inside the container.

Detached mode: Running the container in detached mode allows it to run in the background, freeing up your terminal.
Docker images: The "ollama/ollama" image is pulled from Docker Hub and used to create the container.


Running the OpenWebUI Container
Next, start the OpenWebUI container with the following command:
```
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

This is a Docker command that runs a container with specific settings. Let's break it down:
docker run: Creates and starts a new Docker container.

-d: Runs the container in detached mode (background).

-p 3000:8080: Maps port 3000 on the host machine to port 8080 inside the container.

--add-host=host.docker.internal:host-gateway: Adds a host entry to the container's /etc/hosts file, allowing it to access the host machine's network.

**-v open-webui:/app/backend/data:** Mounts a volume from the host machine to the container:

**open-webui:** Name of the volume on the host machine.

**/app/backend/data:** Path inside the container where the volume is mounted.

**--name open-webui:** Sets the container's name to "open-webui".

**--restart always:** Configures the container to restart automatically if it exits or fails.
(link unavailable): Specifies the Docker image to use (from GitHub Container Registry).

Now, let's guide you through understanding this command:

**Port mapping:** Maps host port 3000 to container port 8080.

**Host entry:** Allows the container to access the host machine's network.

**Volume mounting:** Persists data in the container by mounting a host volume.

**Container naming:** Sets the container's name for easy identification.

**Restart policy:** Configures automatic restarts for the container.

**Docker image:** Specifies the image to use from GitHub Container Registry.

![image](https://github.com/user-attachments/assets/00901ce1-ea4b-40cf-a526-d16e1212f694)

# Step 2: Access the OpenWebUI Interface
Once both containers are running, you can access the OpenWebUI interface through your web browser. Simply navigate to:
```
http://localhost:3000
```
Here, you can interact with the LLM powered by Ollama through a user-friendly web interface.

![image](https://github.com/user-attachments/assets/608a1943-5a6b-416f-a398-3251a2693b57)


# Step 3: Download the Llama Model in the Ollama Container
To download the Llama 3.1 model within the Ollama container, follow these steps:

Open Docker Dashboard: Navigate to your Docker Dashboard or use the command line.

Access the Ollama Container:

Find the ollama container from the list of running containers.
Click on the container to open the details.
Go to the Exec tab (or use docker exec via terminal).
Run the Model Download Command:

In the command input field, type the following command and execute it:
```
ollama run llama3.1
```
This command will initiate the download of the Llama 3.1 model into the container.

Note: If you PC hardware is weak you can run the following model:
```
ollama run phi
```
for list containers 
```
docker container list
```

# Run the Model Download Command:

In the command input field, type the following command and execute it:
```
ollama run llama3.1
```
This command will initiate the download of the Llama 3.1 model into the container.

Note: If you PC hardware is weak you can run the following model:
```
ollama run phi
```
To run the model with the lowest memory usage, use this command:
```
ollama run qwen:0.5b
```
This command tells Ollama to use the qwen:0.5b model, which is designed to work efficiently on computers with low memory.

![image](https://github.com/user-attachments/assets/952d5414-0ace-46f8-ac9a-731a72c55b4c)

Step 4: Verify the LLM is Running
To ensure the LLM is running correctly, you can check the logs of the Ollama container:
```
docker logs ollama
```
You should see the model initialization and any requests being processed. This will confirm that your LLM is up and running smoothly.
