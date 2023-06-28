# Dockerize
#### Dockerize - Building, Testing, and Deploying Applications in Containers.

This GitHub project aims to demonstrate the process of building, testing, and deploying applications in containers using the Docker tool. It consists of several parts.

#### 1. Docker Environment Setup, Container Execution, Dockerfile Customization, Repository Cloning, and Task Submission

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

##### 2. Building and running unit tests within a Docker container.

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


Stworzono Dockerfile, który ma to osiągnąć Na bazie platformowego obrazu... -> doinstalowano wymagania wstępne...


