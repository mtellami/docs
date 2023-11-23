<div align="center">

# 🔥 Containerization 🔥
</div>

Containerization is the packaging of software code with just the operating system (OS) libraries and dependencies required to run the code to create a single lightweight executable—called a container—that runs consistently on any infrastructure. More portable and resource-efficient than virtual machines (VMs), containers have become the de facto compute units of modern cloud-native applications.

Containerization allows developers to create and deploy applications faster and more securely. With traditional methods, code is developed in a specific computing environment which, when transferred to a new location, often results in bugs and errors. For example, when a developer transfers code from a desktop computer to a VM or from a Linux to a Windows operating system. Containerization eliminates this problem by bundling the application code together with the related configuration files, libraries, and dependencies required for it to run. This single package of software or “container” is abstracted away from the host operating system, and hence, it stands alone and becomes portable—able to run across any platform or cloud, free of issues.

The concept of containerization and process isolation is actually decades old, but the emergence in 2013 of the open source Docker Engine—an industry standard for containers with simple developer tools and a universal packaging approach—accelerated the adoption of this technology. Today organizations are using containerization increasingly to create new applications, and to modernize existing applications for the cloud.

## 🔷 Benefits of Containerization
Developers use containerization to build and deploy modern applications because of the following advantages. 

### 🔸 Portability
Software developers use containerization to deploy applications in multiple environments without rewriting the program code. They build an application once and deploy it on multiple operating systems. For example, they run the same containers on Linux and Windows operating systems. Developers also upgrade legacy application code to modern versions using containers for deployment.

### 🔸 Scalability
Containers are lightweight software components that run efficiently. For example, a virtual machine can launch a containerized application faster because it doesn't need to boot an operating system. Therefore, software developers can easily add multiple containers for different applications on a single machine. The container cluster uses computing resources from the same shared operating system, but one container doesn't interfere with the operation of other containers.

### 🔸 Fault tolerance
Software development teams use containers to build fault-tolerant applications. They use multiple containers to run microservices on the cloud. Because containerized microservices operate in isolated user spaces, a single faulty container doesn't affect the other containers. This increases the resilience and availability of the application.

### 🔸 Agility
Containerized applications run in isolated computing environments. Software developers can troubleshoot and change the application code without interfering with the operating system, hardware, or other application services. They can shorten software release cycles and work on updates quickly with the container model.


## 🔷 Containerization use cases
The following are some use cases of containerization.

### 🔸 Cloud migration
Cloud migration, or the lift-and-shift approach, is a software strategy that involves encapsulating legacy applications in containers and deploying them in a cloud computing environment. Organizations can modernize their applications without rewriting the entire software code.

### 🔸 Adoption of microservice architecture
Organizations seeking to build cloud applications with microservices require containerization technology. The microservice architecture is a software development approach that uses multiple, interdependent software components to deliver a functional application. Each microservice has a unique and specific function. A modern cloud application consists of multiple microservices.

### 🔸 IoT devices
Internet of Things (IoT) devices contain limited computing resources, making manual software updating a complex process. Containerization allows developers to deploy and update applications across IoT devices easily.


## 🔷 Building a Container
To talk about containers at the low level, we have to talk about three things. These things are namespaces, cgroups and layered filesystems. There are other things, but these three make up the majority of the magic.

### 🔸 Namespaces
Namespaces provide the isolation needed to run multiple containers on one machine while giving each what appears like it’s own environment. There are - at the time of writing - six namespaces. Each can be independently requested and amounts to giving a process (and its children) a view of a subset of the resources of the machine.

#### - PID
The pid namespace gives a process and its children their own view of a subset of the processes in the system. Think of it as a mapping table. When a process in a pid namespace asks the kernel for a list of processes, the kernel looks in the mapping table. If the process exists in the table the mapped ID is used instead of the real ID. If it doesn’t exist in the mapping table, the kernel pretends it doesn’t exist at all. The pid namespace makes the first process created within it pid 1 (by mapping whatever its host ID is to 1), giving the appearance of an isolated process tree in the container.

#### MNT
The network namespace gives the processes that use it their own network stack. In general only the main network namespace (the one that the processes that start when you start your computer use) will actually have any real physical network cards attached. But we can create virtual ethernet pairs — linked ethernet cards where one end can be placed in one network namespace and one in another creating a virtual link between the network namespaces. Kind of like having multiple ip stacks talking to each other on one host. With a bit of routing magic this allows each container to talk to the real world while isolating each to its own network stack.

#### NET
The network namespace gives the processes that use it their own network stack. In general only the main network namespace (the one that the processes that start when you start your computer use) will actually have any real physical network cards attached. But we can create virtual ethernet pairs — linked ethernet cards where one end can be placed in one network namespace and one in another creating a virtual link between the network namespaces. Kind of like having multiple ip stacks talking to each other on one host. With a bit of routing magic this allows each container to talk to the real world while isolating each to its own network stack.

#### UTS
The UTS namespace gives its processes their own view of the system’s hostname and domain name. After entering a UTS namespace, setting the hostname or the domain name will not affect other processes.

#### IPC
The IPC Namespace isolates various inter-process communication mechanisms such as message queues.

#### USER
The user namespace was the most recently added, and is the likely the most powerful from a security perspective. The user namespace maps the uids a process sees to a different set of uids (and gids) on the host. This is extremely useful. Using a user namespace we can map the container's root user ID (i.e. 0) to an arbitrary (and unprivileged) uid on the host. This means we can let a container think it has root access - we can even actually give it root-like permissions on container-specific resources - without actually giving it any privileges in the root namespace. The container is free to run processes as uid 0 - which normally would be synonymous with having root permissions - but the kernel is actually mapping that uid under the covers to an unprivileged real uid. Most container systems don't map any uid in the container to uid 0 in the calling namespace: in other words there simply isn't a uid in the container that has real root permissions.


### 🔸 CGroups
Fundamentally cgroups collect a set of process or task ids together and apply limits to them. Where namespaces isolate a process, cgroups enforce fair (or unfair - it's up to you, go crazy) resource sharing between processes.

Cgroups are exposed by the kernel as a special file system you can mount. You add a process or thread to a cgroup by simply adding process ids to a tasks file, and then read and configure various values by essentially editing files in that directory.


### 🔸 Layered filesystems
Namespaces and CGroups are the isolation and resource sharing sides of containerisation. They’re the big metal sides and the security guard at the dock. Layered Filesystems are how we can efficiently move whole machine images around: they're why the ship floats instead of sinks.

At a basic level, layered filesystems amount to optimising the call to create a copy of the root filesystem for each container. There are numerous ways of doing this. ```Btrfs``` uses copy on write at the filesystem layer. ```Aufs``` uses “union mounts”. Since there are so many ways to achieve this step.

