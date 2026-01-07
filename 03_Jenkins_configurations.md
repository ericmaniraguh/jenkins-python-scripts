

## **Step 1: Install Docker**

Make sure Docker is installed on your machine.

* Check Docker version:

```bash
docker --version
```

* If not installed, follow [Docker installation guide](https://docs.docker.com/get-docker/).

---

## **Step 2: Create a Docker Network (Optional but Recommended)**

This ensures Jenkins can communicate with other containers later (like Git, Node, or Docker agents).

```bash
docker network create jenkins
```

---

## **Step 3: Create a Volume for Jenkins Data**

To persist Jenkins data even if the container stops:

```bash
docker volume create jenkins_home
```

This will store all Jenkins configs, plugins, and jobs.

---

## **Step 4: Pull the Jenkins Docker Image**

We’ll use the official Jenkins **LTS (Long Term Support)** image:

```bash
docker pull jenkins/jenkins:lts
```

---

## **Step 5: Run Jenkins Container**

Run Jenkins with port mapping and attached volume:

```bash
docker run -d \
  --name jenkins \
  --network jenkins \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

Explanation:

* `-d` → Run in detached mode
* `--name jenkins` → Name the container
* `-p 8080:8080` → Map Jenkins web UI port
* `-p 50000:50000` → Agent communication port
* `-v jenkins_home:/var/jenkins_home` → Persist Jenkins data
* `--network jenkins` → Attach to Docker network

---

## **Step 6: Access Jenkins UI**

* Open browser: [http://localhost:8080](http://localhost:8080)
* Initial password is stored in the container:

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```
* Password generated 
```
89a693348cd44f8aaa8f2a11f3bad26b
```

Copy the password, paste it into the UI, and continue the setup.

---

## **Step 7: Install Suggested Plugins**

During first-time setup, Jenkins will ask to install plugins. Click **“Install suggested plugins”**.
This gives you a ready-to-go setup with popular plugins like:

* Git
* Pipeline
* Docker Pipeline

---

## **Step 8: Create Admin User**

After plugin installation, create your **first admin user**.
Alternatively, continue with the initial admin account.

---

## **Step 9: Verify Jenkins Setup**

Check:

```bash
docker ps
```

You should see Jenkins running.
Test by creating a **sample freestyle project** and running a build.

---

## **Step 10 (Optional): Connect Docker Inside Jenkins**

If you want Jenkins to run Docker commands (for building images or running containers):

1. Run Jenkins container with Docker socket:

```bash
docker run -d --name jenkins --network jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts

```

* Mounting `/var/run/docker.sock` allows Jenkins to control Docker on host.

---

✅ **Now have we have a fully functional Jenkins running in Docker.**

---

