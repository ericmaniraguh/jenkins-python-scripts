

# Jenkins Project Course

![Jenkins Logo](https://www.jenkins.io/images/logos/jenkins/jenkins.png)

**Jenkins** is an open-source automation server that enables you to reliably **build, test, and deploy your software**. It remains one of the most valuable skills for a **DevOps Engineer**, even with newer CI/CD solutions like CircleCI and GitHub Actions.

This project/course demonstrates **setting up Jenkins using Docker**, creating **Freestyle builds**, running **Python scripts**, and configuring **Groovy pipelines** for CI/CD automation.

---

## 📊 Course Overview

* **Views:** 1,178,283
* **Date Published:** June 24, 2022
* **Duration:** ~1 hour

**Why this course matters:**

* Learn to setup and manage Jenkins infrastructure
* Explore Freestyle builds and Groovy pipelines
* Understand Jenkins filesystem, workspace, and build artifacts
* Develop skills to troubleshoot and automate pipelines

---

## 📁 Code Repository

All code, examples, and scripts used in the course are available here:
[https://github.com/devopsjourney1/jenkins-course](https://github.com/devopsjourney1/jenkins-course)

---

## 🛠️ Prerequisites

* Docker installed locally
* Basic knowledge of Git
* Python 3 (optional, for running example scripts)
* Web browser to access Jenkins UI

---

## 📝 Course Chapters

* Jenkins Introduction
* Jenkins TLDR - What is Jenkins?
* Jenkins Infrastructure - Master Server and Agents
* Jenkins Agents - Permanent and Cloud Based
* Freestyle Builds and Pipelines
* Setting up Jenkins using Docker
* Jenkins Web GUI Walkthrough
* Creating a Simple Freestyle Job
* Exploring the Jenkins Filesystem and Workspace
* Freestyle Job - Running Python scripts with Jenkins
* Setting up Docker Cloud Agents
* Jenkins Agent using Docker Desktop Fix
* Docker Agent Template Setup
* Using Labels to Restrict Jobs to Agents
* Setting Builds to be Automatically Triggered on Commits
* Setting up Declarative Pipelines using Groovy
* Using a Jenkinsfile for Pipelines
* Jenkins BlueOcean Overview

---

## 🧰 What You’ll Learn

1. **Jenkins Setup & Docker Integration**

   * Running Jenkins in a Docker container
   * Mapping ports and volumes
   * Accessing Jenkins web GUI

2. **Freestyle Jobs**

   * Creating simple jobs
   * Executing shell scripts
   * Running Python scripts and generating build artifacts

3. **Workspace & Filesystem Exploration**

   * Understanding `/var/jenkins_home/jobs`
   * Viewing `workspace` and build outputs
   * Inspecting `config.xml` and `nextBuildNumber`

4. **Python Automation Scripts**

   * Example: `hello_jenkins.py`
   * Generating `.txt` files during builds
   * Integrating Python scripts in Freestyle jobs

5. **Groovy Pipelines & Jenkinsfile**

   * Declarative pipelines
   * Triggering builds automatically
   * Running multi-stage pipelines

6. **Advanced Jenkins Features**

   * Using agents and labels
   * Docker-based cloud agents
   * BlueOcean visualization
---

## 🚀 Running the Project

1. **Pull the Jenkins Docker image:**

```bash
docker pull jenkins/jenkins:lts
```

2. **Run Jenkins container:**

```bash
docker run -d --name jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

3. **Access Jenkins Web UI:**

```
http://localhost:8080
```

4. **Create a Freestyle Job:**

* Navigate to **New Item → Freestyle Project**
* Add build steps like:

```bash
echo "Hello Jenkins"
echo "Build ID: ${BUILD_ID}"
echo "Build Number: ${BUILD_NUMBER}"
echo "Build URL: ${BUILD_URL}"
python3 hello_jenkins.py
```

5. **View workspace files:**

```bash
cd /var/jenkins_home/workspace/<job-name>
ls -ltra
```

---

## 💡 Tips for Jenkins CI/CD

* Always **archive artifacts** to preserve workspace files
* Configure **Git credentials** to automate pushes
* Explore **BlueOcean** for pipeline visualization

---

## 📌 Note

This project/course is perfect for **DevOps learners**, engineers, or anyone wanting **hands-on Jenkins experience**. Following along will **enhance your CI/CD skills** and prepare anyone for automation in real-world projects.

---
