<img width="813" alt="ps" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/2587ff23-bab4-4213-801d-d567016d8750"><img width="813" alt="ps" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/e3922aed-ead8-4574-86fc-760422de426b"># Docker tutorial
  Docker is a kind of virtual system with the advantage of ease of management. Docker basically consists of docker images and docker containers. A docker container is a environment that runs applications, and a docker images is a read-only template used to build containers.

## Basic commands
  * To check what images are there on the server, use:

  ```linux
  docker images
  ```

  <img width="520" alt="images" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/1fc4f52a-e304-4bd0-8c10-96deed312de7">
  
  * If there is no image that you want to apply, use `docker pull NAME:TAG` to pull a docker image into your server. For example:

  ```linux
  docker pull ubuntu:24.04
  ```

  This may take a while to install. After finish installing, we can use `docker images` to check again if the image is pulled into the server

  <img width="519" alt="pull" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/bae38583-6383-4e2e-a9af-852c555aaef3">

  Note that if the image you want to use is already in the server, you don't need to pull it again.

  * To check all the containers on the server, use:

  ```linux
  docker ps -a
  ```

  <img width="815" alt="ps" src="https://github.com/FeiChinzz/HEPtutorial/assets/131566183/2689e207-b58e-4939-82a9-e1656ab13bae">


## Reference
  <https://hackmd.io/@D2NCN-LxSNiAK6etDgTKYA/r1SNBkokw>
