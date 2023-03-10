# Docker

__Docker__ development began in 2010 and its first market release came into picture in 2013.

Docker is the software that heps [TestNG] build and manage a secure app anywhere, on any platform.

__Before Docker:__

<img src="https://user-images.githubusercontent.com/70295997/208167428-5a46e733-e2e4-4b66-b7ec-6cdaa553b35d.png" width=400>

- On a hardware, install, eg, a Linux OS. On Linux, need to install a software called Hypervisor, which is provided by AWS, Cisco, etc.
	- [Virtual Machine Monitor / Hypervisor](https://www.vmware.com/topics/glossary/content/hypervisor.html):
		- software that creates and runs VMs
		- allows one host computer to support multiple guest VMs by virtually sharing its resources, such as memory and processing

- On a Hypervisor, install particular apps - Tomcat, DB servers (Cassandra, MongoDB and so on), Jenkins, etc.

- Have to create multiple VMs for all the apps on the Hypervisor

- Every VM has its own OS. On a VM I deploy my apps. A VM hosts my OSs.

- All these [virtual] machines are on the same Hypervisor, same Linux OS on some hardware

- From the infrastructire point of view, I have to procure all these VMs and incur extra costs

- Or, I can buy different machines and make them communicate with each other 

- Jenkins is deployed on one server, Tomcat on another server/machine, etc.

- This overall infrastructure is expensive. Have to procure all the hardware, many VMs, and pay for VM services

In 2013, __Docker gets released__.

<img src="https://user-images.githubusercontent.com/70295997/208169393-30c75103-6322-43fb-835b-ff552b20fc69.png" width=500>

Now, there is no need for a Hypervisor or VMs. Use a container with the Docker Engine (a Docker software image).

Eg, I want to install MySQL server. For that I need libraries, binaries, port, IP, etc. I put everything inside an image and upload/install this image on a particular container. Now it runs on a separate service container on this specific Linux machine.

Eg, I want to install the design components of my system - Jenkins, Tomcat, Oracle, Mobile app, etc. 

Design Components:
 - SQL - for DB
 - Jenkins - for CI/CD
 - Tomcat - for App Server, or even DB Server
 - Mobile - for mobile service

Run these machines in separate containers on the same hardware.

1. No need for Hypervisor - no need to spend $$$ on it.
2. No need to create multiple VMs.
3. On the same Linux OS - no need for extra hardware.

But earlier, before Docker, I needed to obtain a Hypervisor. And only then I was able to provide virtualization. The Hypervisor would create multiple VMs on a particular system. Or, I could procure and associate/connect multiple hardware machines, which would be costly.

Docker provides everything in terms of installation and configuration to make sure the app runs. Docker became popular because it's fast, easy to configure and maintain.

Advantages of Docker:
- Isolation of containers. All the containers for MySQL, Tomcat, Jenkins, etc. are isolated, they do not share resources. Resources in terms of RAM, memory, size, etc. No interference/communication among containers. They work independently from each other on a Linux hardware.
- These containerized services can run side-by-side on the same computer. Don't need multiple computers or hardwares.
- Sharing resources on the same OS. But not sharing amoung each other (unless I do specific configurations).
- Containers are isolated and secure. Security being a big factor.
- Less Hardware Concept - no need to get multiple hardwares. Can install many containers on the same machine. Hence, it makes the maintenance easy.

From the shared memory point of view, let's compare Docker and the 'old' way.

![image](https://user-images.githubusercontent.com/70295997/208183556-dcc8fe01-1e18-412c-bb8a-e051337ae218.png)

Re-assignment/re-allocation of the extra/leftover memory is not possible the 'old' pre-Docker way. Saving memory resources is the biggest benefit of Docker Containers. Also, configuration for Docker is easy.

Per Google Trends, the populatiry of Docker has been increasing since its inception.
<img src="https://user-images.githubusercontent.com/70295997/208184761-ce8cd467-43df-45cf-8446-dec9f411c66e.png" width=600>

Advantages:
- Ease of use
- Large Scaling
- Velocity of deployment
- Flexibility
- Microservices architecture

Deploy quickly when I have many deployments on a daily basis. I get better software delivery, velocity, frequent deploys with changes in production. Docker has been used specifically for Microservices (MS).

_How to use Docker for a MS architecture?_ 

Eg, take Google or a similar company that has a HW with many MSs. Each MS does some work, is responsible for its own configuration to provide some data to the users. Let's say I have Backend, MSSQL DB Server, etc., each running on its own [micro] service. Typically, these services are isolated. Each service is hosted on its own Docker container.

![image](https://user-images.githubusercontent.com/70295997/208192937-cd7e41af-7621-4969-9f04-2eb03111382f.png)

Install and run Docker Engine on my (particular HW Linux OS) system. Can do many things through the Docker Engine:

1. Deploy services
2. Maintain
3. Add
4. Update
5. Delete

All these actions are easily handled with Docker container services. The fact that each container is isolated, secure, and has no communication impediments from other containers is very powerful for the MS architecture.

_Why/when not to use Docker?_
- I have an old legacy system which I don't want to touch/disturb. I don't want to change the architecture, deployment strategy, etc.
- Need extra talent, experienced staff who know Docker, containers, virtualization, image creation, DevOps/SRD team collaboration, etc. It's not every developer's niche or responsibility.


__How do Testers / Automation Engineers use Docker?__

In the context of Selenium, I use the Selenium Grid which has a Hub connected to multiple Nodes.

<img src="https://user-images.githubusercontent.com/70295997/208260475-f6b58dd8-36f8-444e-80f3-0cc1772d6f2d.png" width=600>

I install Docker Engine on my machine. Through Docker Engine, I install one Docker Hub container (Selenium Grid Hub). Then, on the same machine I install multiple containers for each browser - Firefox, Chrome, Safari, Opera, etc. I can install all these items with a few simple commands. I can easily stop the Hub, start the server, or disconnect a particular Node.

![image](https://user-images.githubusercontent.com/70295997/208220822-6181d5e3-7964-49c7-8c14-4faa10008af8.png)

The 'old' way maintenance is costly. Need to start the Selenium Grid, make a stop,  restart again, connect the Hub to multiple Nodes. Requires a lot of time and configuration.

The 'new' way avails the one same Docker container running on my (AWS) Linux machine. Eg, I procure one Linux OS server machine on AWS and install my Docker Engine. The Hub uses my Script [from my local Python code] in the form of Desired Capabilities. The Script must include the the IP address and Port number for the Hub I use. I trigger my Test Cases on the Hub, and the Hub distributes them among different Nodes available in the form of different containers. These Nodes do not talk to each other, they are entirely isolated, there are no conflicts.

In Selenium Grid, I can replicate that - no need to have multiple VMs or HWs. That's the biggest advantage of Docker in Test Automation.

Each Docker image is available on www.dockerhub.com, from where I can pull an image and install it. With the image installed, I can use a few commands to install Docker on my system. And automatically Docker takes care of installing the respective libraries, binaries, configuration, environment variables, etc.

Using the 'old' way, with multiple VMs or HWs I had to do everything myself. The 'new' way, I just need to get the right container image and install it on the respective OS. That's the power of Docker. Eg, installing and configuring a SQL Server without Docker is complex. It's simple installing it with the Docker container image. 

I can also handle Jenkins with Docker. I do not need to install Jenkins separately, I just need to install the Jenkins image on my system. One simple command handles everything for Jenkins.


-----

[Deployment Mechanisms and Supportability](https://github.com/lana-20/deployment-mechanisms/tree/main#readme)

[Containerization](https://www.ibm.com/cloud/learn/containerization)

[Containers vs. virtual machines](https://learn.microsoft.com/en-us/virtualization/windowscontainers/about/containers-vs-vm)

[Bare Metal Servers, Virtual Servers, and Containerization](https://www.trustradius.com/buyer-blog/bare-metal-servers-virtual-servers-and-containerization)

[Containerization vs Virtualization](https://www.cloudmanagementinsider.com/containerization-vs-virtualization/)

[Kubernetes CI/CD Pipelines Explained](https://thenewstack.io/kubernetes-ci-cd-pipelines-explained/)

[Understanding Docker](https://dev.to/aurelievache/understanding-docker-part-1-retrieve-pull-images-3ccn)

[How to containerize Python applications with Docker](https://youtu.be/0UG2x2iWerk)

[VMs vs Containers](https://youtu.be/eyNBf1sqdBQ)
