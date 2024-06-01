---
title: "DevDock: Easy Management for Development Containers"
seoDescription: "Effortlessly manage development containers with DevDock for consistent and efficient environments"
datePublished: Sat Jun 01 2024 21:01:59 GMT+0000 (Coordinated Universal Time)
cuid: clwwlmhul000009l42zh96p4b
slug: devdock-easy-management-for-development-containers
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/sWOvgOOFk1g/upload/7b8e59c4258bdc04074ece2743329c5c.jpeg
tags: docker, github, python, opensource, developer, devops, containers

---

I want to share a little adventure I’ve been on - creating a tool called [DevDock](https://github.com/tavallaie/devdock). But first, let me tell you why I started this project and how it makes life easier for developers like you and me.

### The Problem

In our small tech team, we often used Docker images and containers to streamline our development process. However, each time we started a new project or needed to make some tweaks, it was a hassle. We spent a lot of time modifying Docker Compose files or running containers with specific settings. It felt like a never-ending cycle of repetitive tasks, and it was frustrating.

### The Idea

One day, while working late on a project, I was stuck in a loop of updating Docker Compose files and rerunning containers. I thought, "There has to be a better way to do this." That’s when the light bulb went off. What if we could have a tool that made managing these environments as easy as snapping your fingers? A tool that could handle all these tweaks and configurations effortlessly. And that’s how the idea of DevDock was born – a tool to put these tasks right at our fingertips.

### What is a Dev Container?

Think of a dev container as a magic box. You put all your tools, libraries, and dependencies in it, and it keeps them safe and sound. When you open the box, everything is ready to use. It’s like having a personal chef who knows exactly how you like your meals.

### Why Use Dev Containers?

But why should we use dev containers? Let me tell you:

1. **Consistency**: No more “It works on my machine!” Everyone on the team has the same setup.
    
2. **Portability**: Move your project to any computer, and it will work the same.
    
3. **Efficiency**: Saves time and reduces frustration.
    

### Storing Configurations

As we began using dev containers, another realization struck me: having dev containers wasn’t enough. We needed a way to save our ideal setups so that we could recreate them effortlessly. Imagine if you could take a snapshot of your perfectly organized kitchen and set it up exactly the same way anywhere you go. That’s what storing configurations does for dev containers. It keeps your settings, dependencies, and tools saved, ensuring you can set up your development environment quickly and consistently every time.

### The Birth of DevDock

With this realization, I started working on DevDock. My goal was simple: make it easy to create, manage, and store configurations for development containers. Unlike some IDE-specific solutions like what Visual Studio Code offers, I wanted DevDock to be IDE-independent. This way, developers using any code editor or IDE could benefit from a smooth, consistent development environment. I spent days coding, testing, and fixing bugs. There were challenging moments, but I kept going, motivated by the thought of making life easier for my fellow developers.

### Features of DevDock

1. **Create Containers**: Easily create containers with all the tools and dependencies you need.
    
2. **Store Configurations**: DevDock stores your configurations in a simple YAML file. This means you can recreate your environment anytime, anywhere.
    
3. **Manage Volumes**: Need to save data inside your container? No problem! DevDock helps you manage volumes too.
    
4. **Support for Docker Compose**: If you have a complex setup with multiple services, DevDock supports Docker Compose, making it easy to manage.
    
5. **IDE Independence**: Unlike VS Code’s built-in dev containers, DevDock works with any IDE or code editor.
    

### Using DevDock

Using DevDock is super simple. Here’s how you can start your own journey with DevDock:

1. **Install DevDock**:
    
    ```bash
    pip install devdock
    ```
    
2. **Create a Container from an Image**:
    
    ```bash
    devdock mkdevcontainer --image python:3.9 --name my-python-container --volumes /host/path1:/container/path1,/host/path2:/container/path2
    ```
    
    Imagine you need a Python environment for a new project. With DevDock, you can create a container with Python 3.9 and map your local directories to the container effortlessly.
    
3. **Run Services from a Docker Compose File**:
    
    ```bash
    devdock mkdevcontainer -f docker-compose.yaml --name my-compose --volume-mappings web:/host/path1:/var/www,web:/host/path2:/var/log/nginx,redis:/host/redis1:/data,db:/host/db1:/var/lib/postgresql/data
    ```
    
    Suppose you have a web project that also needs Redis and a PostgreSQL database. Using DevDock, you can specify your Docker Compose file and add volume mappings for each service, making the setup process a breeze.
    
4. **Activate a Configuration**:
    
    ```bash
    devdock workon my-compose
    ```
    
    Once your environment is set up, you can activate it with a single command. DevDock will start all the services defined in your configuration, so you can get to work immediately.
    
5. **Activate Specific Services**:
    
    ```bash
    devdock workon my-compose --services web
    ```
    
    If you only need to work on the web service, DevDock can activate just that service along with its dependencies, saving you resources and startup time.
    
6. **Run a Command Inside a Specific Service**:
    
    ```bash
    devdock run my-compose --service web "echo Hello, World!"
    ```
    
    Need to run a command inside the web service? DevDock makes it simple. Just specify the service and the command, and DevDock takes care of the rest.
    
7. **Enter Shell Inside a Specific Service**:
    
    ```bash
    devdock shell my-compose --service web
    ```
    
    For more interactive work, you can enter a shell inside any service. This is great for debugging or making quick changes.
    
8. **Remove a Configuration**:
    
    ```bash
    devdock rmdev my-compose
    ```
    
    When you're done with a project, you can clean up easily. DevDock removes all the containers and configurations associated with your project, keeping your system tidy.
    

### Join the Adventure

Creating DevDock has been an incredible journey. It started with a simple idea and grew into a tool that can help developers everywhere. Now, with DevDock, you can manage your dev containers with ease, save your configurations, and never worry about setting up your environment again.

If you’re a developer looking for a smoother workflow, give DevDock a try. I promise, it will make your coding life a lot easier. And who knows, you might just fall in love with it as much as I did.

I would love your feedback and contributions. If you have any ideas, suggestions, or find any issues, please visit our GitHub repository. Your contributions will help make DevDock even better.

**GitHub Repository**: [DevDock GitHub Repository](https://github.com/tavallaie/devdock)

If you have any questions or need help, feel free to reach out. I’m always happy to help fellow developers.