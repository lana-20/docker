# Docker

__Docker__ development began in 2010 and its first market release came into picture in 2013.

Docker is the software that heps [TestNG] build and manage a secure app anywhere, on any platform.

__Before Docker:__

<img src="https://user-images.githubusercontent.com/70295997/208167428-5a46e733-e2e4-4b66-b7ec-6cdaa553b35d.png" width=400>

- On a hardware, install, eg, a Linux OS. On Linux, need to install a software called Hypervisor (VMWare), which is provided by AWS, Cisco, etc.
	- [VMWare / Virtual Machine Monitor / Hypervisor](https://www.vmware.com/topics/glossary/content/hypervisor.html):
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





-----

[Containerization](https://www.ibm.com/cloud/learn/containerization)

[Containers vs. virtual machines](https://learn.microsoft.com/en-us/virtualization/windowscontainers/about/containers-vs-vm)

[Bare Metal Servers, Virtual Servers, and Containerization](https://www.trustradius.com/buyer-blog/bare-metal-servers-virtual-servers-and-containerization)

[Containerization vs Virtualization](https://www.cloudmanagementinsider.com/containerization-vs-virtualization/)


