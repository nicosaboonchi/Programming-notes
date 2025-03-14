# 🚀 Docker Notes

## 📌 What is Docker?

Docker is a **virtualization platform** that makes developing and deploying applications easier by packaging everything into **containers**.

### 🔹 Key Benefits of Docker

- **Portable** → Runs the same way across different environments.
- **Lightweight** → Uses fewer resources than virtual machines.
- **Self-sufficient** → Packages applications with all dependencies, configurations, system tools, and runtime.
- **Faster Deployment** → Simplifies setup and reduces compatibility issues.

---

## 🔥 How Did Deployment Work Before Docker?

### 🛑 The Old Way

Before Docker, developers had to manually install and configure everything on their local machines:

- Different OS environments caused inconsistencies.
- Software versions often mismatched across environments.
- Configuration issues led to deployment failures.

### 🔄 Deployment Process Before Docker

1️⃣ Create a deployment artifact (e.g., compiled code, scripts).  
2️⃣ Write installation and configuration instructions.  
3️⃣ Hand it over to the **Operations (Ops) team**.  
4️⃣ The Ops team manually installs and configures the software on the server.

💡 **Problem:** Manual setup = **high risk of errors, longer deployment times, and inconsistencies**.

---

## 🚀 How Docker Improves Deployment

### ✅ The New Way – Deployment with Containers

With Docker, everything an application needs is inside a **Docker image**. The deployment process is much simpler:  
1️⃣ **Build** a container image with all dependencies.  
2️⃣ **Push** the image to a Docker registry (e.g., Docker Hub).  
3️⃣ **Run** the container anywhere using a single command.

```bash
docker run -d -p 8080:80 my-container
```

# 🐳 Docker vs 🖥️ Virtual Machines (VMs)

## 🏗️ Understanding the Kernel

- The **kernel** is the core of every operating system.
- It acts as a bridge between the **hardware** and **software** of a computer.

---

## 🔍 What Part of the OS Do They Virtualize?

| **Feature**              | **Docker (Containers)**  | **Virtual Machines (VMs)**     |
| ------------------------ | ------------------------ | ------------------------------ |
| **Virtualization Layer** | OS **application layer** | **Kernel & application layer** |
| **Size**                 | Small (a few MBs)        | Large (several GBs)            |
| **Startup Time**         | **Fast** – takes seconds | **Slow** – takes minutes       |
| **OS Compatibility**     | Primarily Linux-based    | Supports all operating systems |

### 📌 Why Is Docker Smaller & Faster?

- Docker **shares the host OS kernel**, while VMs need a **full OS installation** inside each instance.
- This makes **Docker containers lightweight**, whereas VMs require **gigabytes of storage**.

---

## 🚀 Speed Comparison

| **Metric**         | **Docker (Containers)**            | **VMs**                         |
| ------------------ | ---------------------------------- | ------------------------------- |
| **Startup Time**   | ⚡ **Seconds**                     | 🕐 **Minutes**                  |
| **Resource Usage** | 🚀 **Lightweight** (shares kernel) | 🏋️ **Heavy** (requires full OS) |

---

## 🏆 Compatibility: Docker vs. VMs

| **Feature**        | **Docker**                                 | **VMs**                                        |
| ------------------ | ------------------------------------------ | ---------------------------------------------- |
| **OS Support**     | ✅ Works on **Linux** natively             | ✅ Supports **all OS** (Windows, macOS, Linux) |
| **Cross-Platform** | ⚠️ Limited – mostly Linux-based containers | ✅ Full OS flexibility                         |

### 🔹 Why Is Docker Mostly Linux-Based?

- Most **Docker containers** are built for **Linux** environments.
- **Docker was originally designed for Linux**, so it integrates best with Linux kernels.
- **Docker Desktop** allows running Linux containers on **Mac & Windows** by using a **lightweight virtualized Linux environment**.

---

## 🔧 How Does Docker Work on Mac & Windows?

Docker uses a **hypervisor layer** along with a lightweight Linux distribution to run Linux containers on non-Linux systems.

### 🔹 Virtualization Used by Docker on Different Platforms:

| **Host OS**       | **Virtualization Method**                                                    |
| ----------------- | ---------------------------------------------------------------------------- |
| **Linux**         | Uses the native Linux kernel (no extra virtualization)                       |
| **Windows & Mac** | Uses **Docker Desktop**, which runs a lightweight Linux VM in the background |

---

## 🔗 Additional Resources

📖 [Official Docker Documentation](https://docs.docker.com/)  
🎥 [Docker vs VM Video (YouTube)](https://www.youtube.com/results?search_query=docker+vs+vm)  
📝 [Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)

# 🚀 Installing Docker

1️⃣ Go to the official **Docker website** [Docker Downloads](https://www.docker.com/get-started).  
2️⃣ Follow the installation steps provided for your specific OS.  
3️⃣ Check the **system requirements** to ensure compatibility.

---

# 🖼️ Images vs. 🛠️ Containers

### **Image**

- Contains an **executable application artifact** (e.g., source code, configuration files).
- Includes the **complete environment configuration**, such as dependencies and system tools.
- Can define environment variables, create directories, and modify files.
- Immutable template that defines how a container will run.

### **Example of an Image**

- **Application**: JavaScript (JS) app
- **Services Needed**: Node.js, npm
- **OS Layer**: Linux

### **Container**

- A **running instance** of an image.
- **Starts the application** defined within the image.
- You can run **multiple containers** from a single image.

---

## 🖼️ Docker Commands

### **List Docker Images**

```bash
docker images
```

- Displays all available Docker images on your system

### **List of Docker Containers**

```bash
docker ps
```

- Displays all running containers with their details (container ID, names, and ports)

# 🗄️ Docker Registry

## 📌 What is it?

- A **storage** and **distribution system** for Docker images.
- Official images for popular applications (e.g., Redis, MongoDB, PostgreSQL) are available.
- Official images are maintained either by **software authors** or in collaboration with the **Docker community**.
- [**Docker Hub**](https://hub.docker.com/) is one of the largest and most well-known Docker registries.

---

# 🏷️ Image Versioning

- Docker images are **versioned** to track changes and updates.
- Different versions of an image are identified by **tags**.
- A special tag called **`latest`** refers to the most recent version of the image.
  - If you don’t specify a tag when pulling an image, Docker will automatically fetch the **`latest`** version.

---

# 📥 Downloading an Image

To pull an image from a registry, use the following command:

```bash
docker pull {name}:{tag}
```

- **`{name}`**: The name of the image (e.g., mongo, redis).
- **`{tag}`**: The version tag (e.g., latest, 4.0, alpine)
- Example:

```bash
docker pull redis:latest
```

- This command pulls the latest version of the Redis image.

---

# 🚀 Running an Container

To create a container from a given image and start it, use the following command:

```bash
docker run {name}:{tag}
```

- **`{name}`**: The name of the image (e.g., mongo, redis).
- **`{tag}`**: The version tag (e.g., latest, 4.0, alpine)

---

# 👀 See the Running Containers

To view the containers currently running:

```bash
docker ps
```

- This will list all running containers with details like container ID, names, and exposed ports.

---

# 🔙 Running Containers in the Background

By default, `docker run` will block the terminal and run the container in the foreground. To run the container in the background, use the `-d` or `--detach` flag:

```bash
docker run -d {name}:{tag}
```

- `{name}`: The name of the image (e.g., nginx).
- `{tag}`: The version or tag of the image (e.g., 1.23).
- This command runs the container in the background and prints the container ID.

---

# 📝 Viewing Logs

If you want to see the logs of a running container, use the following command:

```bash
docker logs {container}
```

- `{container}`: The container ID or name.
- This shows the logs from the service running inside the container, which is helpful for troubleshooting

---

# ⚡ Skipping the Image Pull

- If the image is not already available locally, Docker will automatically pull the image from the registry before starting the container.
- The following command ensures that the image is pulled (if not already available) and runs the container

```bash
docker run {name}:{tag}
```

- `{name}`: The name of the image (e.g., nginx).
- `{tag}`: The version or tag of the image (e.g., 1.23).

---

# 🔌 Port Binding

## 🆚 Container Vs Host Port

- The application inside a container runs in an **isolated Docker network**, meaning it can operate independently of other applications.
  - This allows us to run multiple instances of the same app on the same port without conflict.
- To make the application accessible outside the container, we need to **expose the container's port to the host** (the machine the container runs on).
- **Port Binding:** This process binds the container's internal port to a port on the host, making the service available to the outside world.

---

## 📡 Publish Container's Port to the Host

To publish a container's port to the host, use the `-p` or `--publish` option with the `docker run` command:

```bash
docker run -d -p {host port}:{container port} {name}:{tag}
```

- `{host port}`: The port on the host machine (e.g., 9000).
- `{container port}`: The port inside the container (e.g., 80).
- `{name}`: The name of the image (e.g., nginx).
- `{tag}`: The version or tag of the image (e.g., 1.23).

### Example:

```bash
docker run -d -p 9000:80 nginx:1.23
```

- This command runs the nginx container in detached mode and binds port 9000 on the host to port 80 inside the container, making the web service available on the host's port 9000.
- **As a standard use the same port on your host as your container**

# 🚦 Start and Stop Containers

- Docker creates a new container every time you run a command; it **does not re-use** previous containers.

---

## 📝 View List of All Containers

To view a list of all containers (both running and stopped), use the `-a` or `--all` flag:

```bash
docker ps -a
```

- This command will display a list of all containers, including their status (running or stopped).

## 🛑 To Stop a Container

To sotp a running container, use the following command:

```bash
docker stop {container}
```

- Replace {container} with the container ID or name of the container you want to stop.

## ▶️ To Start One or More Stopped Containers

To start a container that has been stopped, use:

```bash
docker start {container}
```

- Replace {container} with the container ID or name of the stopped container.

## 🏷️ To Assign a Container a Name

To assign a custom name to a container during creation, use the `--name` flag:

```bash
docker run --name {name} -d -p 9000:80 nginx:1.23
```

- `--name {name}`: Assigns the specified name to the container (e.g., `{name}`).
- `-d`: Runs the container in detached mode (background).
- `-p 9000:80`: Maps port 9000 on the host to port 80 in the container

# 📦 Registry vs Repository

## 🏢 Registry

- A **service** that provides **storage** for Docker images.
- Can be hosted by:
  - Third-party services (e.g., AWS, Docker Hub, Azure).
  - Your own self-hosted registry.
- A **Registry** is a **collection of repositories**.

## 📂 Repository

- A **collection of related images** that share the same name but have different versions.
- Each image is identified by a **tag** (e.g., `1.0`, `latest`).

---

# 🛠️ Creating Custom Images

## Why Create a Custom Image?

- After finishing an application, we need to package it into an image for deployment.
- A **Dockerfile** is required, which is a **text document** containing instructions to build an image.
- Docker reads the **Dockerfile** and builds an image accordingly.

---

## 📜 Create the `Dockerfile`

### 🏗️ **FROM** – Define the Base Image

- Every `Dockerfile` starts with a **parent/base image**.
- This is the foundation on which our image is built.

#### Example:

```dockerfile
FROM node:19-alpine
```

- Uses the official Node.js 19 Alpine Linux image as the base.

---

### 📂 COPY – Copy Files from Host to Containe

Copies files from the host machine to a specified location in the container

```dockerfile
COPY <src> <dest>
```

#### Example:

```dockerfile
COPY package.json /app/
COPY src /app/
```

---

### 📍 WORKDIR – Set Working Directory

Sets the working directory for subsequent commands

#### Example:

```dockerfile
WORKDIR / app;
```

- All following commands will run inside `/app/`

---

### ⚙️ RUN – Execute Commands Inside the Container

Runs shell commands inside the container at build time.

#### Example:

```dockerfile
RUN npm install
```

- Installs dependencies inside the container

---

### 🚀 CMD – Define the Startup Command

- Specifies the default command that runs when the container starts.
- Can only be one `CMD` instruction per `Dockerfile`

#### Example:

```dockerfile
CMD[("node", "server.js")];
```

- Runs node server.js when the container starts

---

## 🏗️ Build the Image

To build a Docker image from a `Dockerfile`, use:

```bash
docker build -t <name>:<tag> <Dockerfile path>
```

#### Example:

```bash
docker build -t node-app:1.0 .
```

- `-t node-app:1.0` → Names the image node-app with the tag 1.0.
- `.` → Specifies the current directory as the build context.
