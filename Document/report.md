# Database

# 1-1 For which reason is it better to run the container with a flag -e to give the environment variables rather than put them directly in the Dockerfile ?

It's better to to the container with the -e flag just in case if someone has access to the Dockfile for security. If he can access this file, he can check all the image history and see the password plaintext.

# 1-2 Why do we need a volume to be attached to our postgres container ? 

Our postgres container contains data and if stop the container, all the data will be erased so to keep the data, we use volumes to make sure that data is stored outside the container, on the host machine or Docker-managed storage.

# 1-3 Document your database container essentials: commands and Dockerfile.

# 1-4 Why do we need a multistage build? And explain each step of this dockerfile. 

A multistage build can be usefull because it can help to write a readable Dockerfile but howerver the main purpose of this build is to simplified the file and to leave behind the JDK and Maven to just let the JRE in the final image.

# 2-1 What are testcontainers?
Testcontainers is a library that provides an interface to run and write your integration test.

# 2-2 For what purpose do we need to use secured variables ?

They are usefull to protected sensible data such as password , Token etc...

# 2-3 Why did we put needs: build-and-test-backend on this job? Maybe try without this and you will see!








# 2-1 What are testcontainers?

Testcontainers is basically just a Java library that provide you simple interface to write and un run your integration test.
