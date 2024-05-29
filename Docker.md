# Docker tutorial
  Docker is a kind of virtual system with the advantage of ease of management. Docker basically consists of docker images and docker containers. A docker container is a environment that runs applications, and a docker images is a read-only template used to build containers.

## Basic commands
  * To check what images are there on the server, use:

  ```linux
  docker images
  ```

  <img width="520" alt="images" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/1fc4f52a-e304-4bd0-8c10-96deed312de7">
  
  * If there is no image that you want to apply, use the following to pull a docker image into your server:

  ```linux
  docker pull NAME:TAG
  ```

  For example, I pulled the image `ubuntu:24.04` into the sever. This may take a while to install. After finish installing, we can use `docker images` to check again if the image is pulled into the server

  <img width="519" alt="pull" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/bae38583-6383-4e2e-a9af-852c555aaef3">

  Note that if the image you want to use is already in the server, you don't need to pull it again.

  * To check all the containers on the server, use:

  ```linux
  docker ps -a
  ```

  <img width="815" alt="ps" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/2689e207-b58e-4939-82a9-e1656ab13bae">

## Create container

  * To create a container, use:

  ```linux
  docker run --name CONTAINERNAME --net=host -v SERVER_PATH:CONTAINER_PATH -it IMAGENAME:TAG
  ```

  There are some command to explain:

  1. `--name CONTAINERNAME` : To give the container a name.
  2. `-net=host` : To make the internet setting of container is the same as the server.
  3. `-v SERVER_PATH:CONTAINER_PATH` : To create a tunnel between the server and the container. Usually, this tunnel is created to store the data.
  4. `-it IMAGENAME:TAG` : To specify the image you want to copy. Before creating the container, you should make sure the image is already pulled to your server.

  For example, we create a container using the image `feichinzz/ubuntu:MG5tools` as following:
  
  ```linux
  docker run --name Tutorial_test --net=host -v /data1/Chen-Wang:/data -it feichinzz/ubuntu:MG5tools
  ```

  <img width="710" alt="run" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/26cf2ec4-447e-4124-98e6-aa73975a71a6">

  After creating the container, you will directly enter the container (notice that the title of command line changes). Use `ls -l` to check if the tunnel is established successfully:

  <img width="382" alt="check_data" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/4b8c4ca0-94c8-409c-98f8-28b2efeeba57">

  This image contains lots of HEP tools for simulation, including MadGraph, Pythia, Delphes, also python2, python3, jupyter lab. The mainly used application for simulation is Madgraph, where the path is in `~/MG5_aMC_v2_7_3/`:

  <img width="472" alt="MG5" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/50832065-4390-4495-878f-87244224c0dd">

  * To leave the container, use:

  ```linux
  exit
  ```

  <img width="207" alt="leave" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/791f9a1e-da33-4927-b0d6-23028552252f">

  Now, we leave the container and go back to the server, we can use the command `docker ps -a` to check if our container is successfully created:
  
  <img width="834" alt="created" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/648e82cf-d060-4106-8364-16d691651bdd">

## Enter the leave the container

  * To enter a container that has already been created, you don't need to use `docker run ...` again. Instead, we use:

  ```linux
  docker start CONTAINERNAME
  ```
  
  to start the container. Then, use:

  ```linux
  docker attach CONTAINERNAME
  ```

  to get into the container. For example, I want to get into the creadted container `Tutorial_test`:

  <img width="286" alt="start" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/7e971b33-3c1d-4378-8289-f68d46987852">

  Now, we re-enter the container.

  * To leave and close the container, just use the command:

  ```linux
  exit
  ```


## Reference
  <https://hackmd.io/@D2NCN-LxSNiAK6etDgTKYA/r1SNBkokw>
