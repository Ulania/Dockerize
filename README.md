# Dockerize
#### Dockerize - Building, Testing, and Deploying Applications in Containers.

This GitHub project aims to demonstrate the process of building, testing, and deploying applications in containers using the Docker tool. It consists of several parts.

### 1. Docker Environment Setup, Container Execution, Dockerfile Customization, Repository Cloning, and Task Submission

1. Running busybox.
Displaying the container execution result.
Connecting interactively to the container and retrieving the version number.
![5](https://github.com/Ulania/Dockerize/assets/96245511/76d37ed4-446c-480d-a81b-334f55fb5e7f)

2. Running "system in the container".
Presenting PID1 in the container and Docker processes on the host.
![6](https://github.com/Ulania/Dockerize/assets/96245511/bee0e8e7-e3ee-4f1e-9ebc-a5119830e42d)

3. Manually creating, building, and running a simple Dockerfile based on the chosen system and cloning the repository.
![8](https://github.com/Ulania/Dockerize/assets/96245511/aa8829d2-94e4-49c8-bcae-4a68bcda45b5)



    ![9](https://github.com/Ulania/Dockerize/assets/96245511/b156c29f-639b-4caa-b325-cbc85fddeb75)

    Running in interactive mode and verifying that the repository has been successfully downloaded.
    ![10](https://github.com/Ulania/Dockerize/assets/96245511/d85fe547-f579-4ba0-9143-5efa212b95a0)


#### 2. Building and running unit tests within a Docker container.
A project called "Calculator" was found on GitHub, which allows for easy execution of unit tests.

1. The environment has been prepared for the tested project to run
![2](https://github.com/Ulania/Dockerize/assets/96245511/d27f8a6a-84ba-4857-9d72-ce17b8f627af)

2. Running unit tests.
![3](https://github.com/Ulania/Dockerize/assets/96245511/b82e4433-86a4-4ab3-850e-9997c2d707ca)

3. Repeating the process within a container.
->Supplying the platform with the necessary prerequisite software:
![4](https://github.com/Ulania/Dockerize/assets/96245511/776b5473-1f90-4dd1-b784-3b2c5129ea11)

    ->Cloning the application:
![5](https://github.com/Ulania/Dockerize/assets/96245511/8e884f4c-4be0-42c5-91df-541bdb20c63c)

    ->Environment setup and build execution:
![6](https://github.com/Ulania/Dockerize/assets/96245511/129491b0-e7ff-412a-bfd0-9ff229efbe56)

    ->Tests executed:
![10](https://github.com/Ulania/Dockerize/assets/96245511/978c2460-fa79-4add-b30e-341351c6aef2)

4. The process was repeated inside a container.
-> The repository has been cloned and the code has been built:
![11](https://github.com/Ulania/Dockerize/assets/96245511/d7115fbe-7115-4ec1-98b2-2e3f41398d63)

    ->Compilation:
![13](https://github.com/Ulania/Dockerize/assets/96245511/cb0ce6b0-fbb0-4ec1-b910-99363f58b81d)

5. Based on the image created by the previous Dockerfile, another Dockerfile has been created to run tests
-> The first container performs all the steps up to the build:
![14](https://github.com/Ulania/Dockerize/assets/96245511/3734a70d-ab54-417b-9515-5fd241a22aba)

    -> The second container is based on the first one and executes the tests:
![15](https://github.com/Ulania/Dockerize/assets/96245511/b32b78e8-360a-4c8d-aa25-3e176ffba58a)

    -> Compilation and testing:
![16](https://github.com/Ulania/Dockerize/assets/96245511/ee2e1466-1290-46c3-8aed-ffdaf81f51ce)

    Content of Dockerfiles:
    a. dockerfile_lab3:
![17](https://github.com/Ulania/Dockerize/assets/96245511/0639b2b5-e50e-44ad-b539-362ab2878776)

   b. dockerfile_lab3_test
![18](https://github.com/Ulania/Dockerize/assets/96245511/e557998d-c56d-4ccc-94c0-e641e2da1dc5)


### 3. Exploring state persistence in Docker containers and exposing ports for communication with database applications.

1. A database container was created without a volume.
![1](https://github.com/Ulania/Dockerize/assets/96245511/547f4d67-d3f1-4561-8341-699d0e1da503)

The PostgreSQL image was downloaded from Docker Hub.

2. Operations were performed on the database:

    -> An interactive psql session was started in the "postgresql" Docker container, connecting to the PostgreSQL server running inside the container.
![3](https://github.com/Ulania/Dockerize/assets/96245511/0c1ded92-8408-4041-a251-5675bd87c952)
    -> Tables and data were added to the database using CLI (Command Line Interface) communication.
![3 1](https://github.com/Ulania/Dockerize/assets/96245511/6cac4aa2-3072-42c8-a887-cc0cc13a3fd9)

3. The container was deleted and then recreated from the same image.
![4](https://github.com/Ulania/Dockerize/assets/96245511/368072aa-276a-4c0c-ba94-b3be964d20fd)

As seen in the screenshot, the table does not exist.

4. The same container was recreated with a volume attached, where the volume was mounted to the data directory of the database.

![5](https://github.com/Ulania/Dockerize/assets/96245511/6e42d266-fe65-4ca7-8b5b-c78990fe5f7b)
   
The following command was used:
```docker run --name postgresql -e POSTGRES_PASSWORD=your_password -p 5432:5432 -v pgdata:/var/lib/postgresql/data -d postgres```

This command launched the PostgreSQL container and attached it to a volume named "pgdata". This ensures that the database data is stored on the host disk and will not be lost when the container is deleted.

5. Changes were made to the database (tables and data were added), saved, and then the container was deleted.
![6](https://github.com/Ulania/Dockerize/assets/96245511/33e5d04e-578a-4c65-b7f1-cedd1acc7b95)

6. The container was recreated again with the same volume attached.
The changes were preserved thanks to the volume since volumes are persistent storage that remains even after stopping or removing the container.
![7](https://github.com/Ulania/Dockerize/assets/96245511/3262f762-c226-401d-b62a-f6b7aace8600)

For stateful applications, it is usually recommended to use sessions to store user data between HTTP requests. In such cases, increasing the cache size (volume) can significantly improve application performance. Stateless applications do not require storing state information on the server. For such applications, there is no need to increase the cache size as they do not store data between requests.

Port Exposing:

DBeaver was downloaded.
![8](https://github.com/Ulania/Dockerize/assets/96245511/61d13d3d-9d04-4126-b003-dff40e20bbdb)

1. A container was prepared with port forwarding for the database container (exported the database port).
![9](https://github.com/Ulania/Dockerize/assets/96245511/5331a80d-40ce-4b30-8ea1-16ed84eaaa59)

![10](https://github.com/Ulania/Dockerize/assets/96245511/74d9f6e0-bde6-4e34-92d5-9aa0b56e6c0d)

3. Using the exported port, a connection was established with the database using a local (non-containerized) client such as DBeaver.

    -> Connection testing to the database was performed.
    -> Database operations, including creating tables and adding data, were executed.
4. A second container was created with a database client.

![11](https://github.com/Ulania/Dockerize/assets/96245511/69f58507-898f-4797-9cba-b10781373d34)

![11 1](https://github.com/Ulania/Dockerize/assets/96245511/392bd0ca-c410-45a8-91b3-62e2aa3e8dd9)

5. Using the CLI in the second container, a connection was established with the database in the first container.
![12](https://github.com/Ulania/Dockerize/assets/96245511/1f0ea5b4-fc3d-40e8-8da4-3aa951e5022c)

Initially, a container with the PostgreSQL image was launched, and after logging into it, the postgresql-client was installed. Then, a successful connection was made to the database running in the first container.

7. Database operations (adding a row) were executed using the second container's CLI, and the changes were verified using the database client.
![13](https://github.com/Ulania/Dockerize/assets/96245511/840489da-9cc6-4f33-9e10-55b6d3ef2e79)

