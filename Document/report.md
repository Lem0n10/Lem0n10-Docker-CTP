# DevOps TP Report

## Docker

### 1-1 Why is it better to use the -e flag for environment variables rather than putting them directly in the Dockerfile?

Using the -e flag is better for security and flexibility. Dockerfiles are usually versioned in Git, so hardcoding passwords shows clearly sensitive data in the repository history.

### 1-2 Why do we need a volume attached to our postgres container?

Docker containers are ephemeral and when we destroyed them, all internal data is lost. 

Without a volume, the database would reset every time when the container is recreated. Volumes mount host directories to the container's data directory, ensuring data persistence across container lifecycles.

### 1-4 Why do we need a multistage build? Explain each step of this dockerfile.

Multistage builds can help to reduce image size and improve security by separating build tools from the runtime environment. The final image only contains the JRE and compiled application and not Maven or the full JDK.

### 1-5 Why do we need a reverse proxy?

A reverse proxy provides a single entry point for all services, handles SSL/TLS termination in one place, enables load balancing across multiple backend instances, improves security by hiding implementation details and filtering requests, can serve static content(frontend), and simplifies port management by exposing only ports 80/443.

### 1-6 Why is docker-compose so important?

Docker-compose simplifies multi-container orchestration by defining all services in one YAML file and launching everything with a single command.

### 1-10 Why do we put our images into an online repo?

We put images on online repositories because it enable team collaboration by sharing standardized images, simplify deployment across different servers, provide version control and history which is essential for CI/CD pipelines by serving as centralized backups and ensuring consistency. 

In addition, everyone can use exactly the same images even if the don't use the same machine.


## GitHub Actions

### 2-1 What are testcontainers?

Testcontainers are Java libraries that launch Docker containers during test execution. They also provide real database instances ensuring realistic integration tests. 

Containers are automatically created before tests and destroyed after, providing complete isolation and eliminating manual setup which makes tests more reliable and portable.

### 2-2 For what purpose do we need to use secured variables?

Secured variables protect sensitive credentials such as DockerHub tokens from exposure in source code. Since GitHub provides access control, only authorized workflows can use secrets and they're masked in logs.

### 2-3 Why did we put needs: build-and-test-backend on this job?

The needs directive creates a dependency between jobs ensuring tests pass before building and pushing images. 

Without needs, jobs may run in parallel potentially pushing broken images to DockerHub before knowing if tests works or not. This follows the logical CI/CD flow prevents publishing broken images, and saves resources by avoiding unnecessary builds when tests fail.

### 2-4 For what purpose do we need to push docker images?

Pushing images:
- Enables automated deployment to servers
- Supports CD with tools like Ansible
- Provides version history of deployable releases
- Allows team-wide sharing of standardized images
- Ensures reproducibility


## Ansible

### 3-1
