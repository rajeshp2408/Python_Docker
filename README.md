"# Python_Docker" 

Docker build
D:\Python_Docker\1_Python_Script_Docker>docker build -t python_hello .
[+] Building 16.6s (10/10) FINISHED                                                                                                      docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                                                                     0.0s
 => => transferring dockerfile: 182B                                                                                                                     0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                         3.1s
 => [internal] load .dockerignore                                                                                                                        0.0s
 => => transferring context: 2B                                                                                                                          0.0s
 => [1/5] FROM docker.io/library/ubuntu:latest@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30                                   0.0s
 => [internal] load build context                                                                                                                        0.0s
 => => transferring context: 28B                                                                                                                         0.0s
 => CACHED [2/5] RUN apt update                                                                                                                          0.0s
 => [3/5] RUN apt install python3 -y                                                                                                                    12.5s
 => [4/5] WORKDIR /usr/app/src                                                                                                                           0.1s
 => [5/5] COPY main.py ./                                                                                                                                0.2s
 => exporting to image                                                                                                                                   0.5s
 => => exporting layers                                                                                                                                  0.4s
 => => writing image sha256:bbe4b526ef6ed68adfdc7ba2ad9dafd97d5189164bd0af00decfe8d54d1b3d2e                                                             0.0s
 => => naming to docker.io/library/python_hello                                                                                                          0.0s

D:\Python_Docker\1_Python_Script_Docker>docker images
REPOSITORY     TAG       IMAGE ID       CREATED         SIZE
python_hello   latest    bbe4b526ef6e   8 seconds ago   155MB

D:\Python_Docker\1_Python_Script_Docker>
D:\Python_Docker\1_Python_Script_Docker>docker run python_hello
Hello World!

D:\Python_Docker\1_Python_Script_Docker>

D:\Python_Docker\1_Python_Script_Docker>docker run -it python_hello /bin/bash
root@75167bd3c633:/usr/app/src# ls
main.py
root@75167bd3c633:/usr/app/src# cat main.py
def print_func():
    print("Hello World!")


if __name__=="__main__":
    print_func()

root@75167bd3c633:/usr/app/src#
	
	
root@75167bd3c633:/usr/app/src# cd ..
root@75167bd3c633:/usr/app# ll
total 20
drwxr-xr-x 1 root root 4096 Jun 25 05:21 ./
drwxr-xr-x 1 root root 4096 Jun 25 05:21 ../
drwxr-xr-x 1 root root 4096 Jun 25 05:21 src/
root@75167bd3c633:/usr/app# ll src/
total 16
drwxr-xr-x 1 root root 4096 Jun 25 05:21 ./
drwxr-xr-x 1 root root 4096 Jun 25 05:21 ../
-rwxr-xr-x 1 root root   92 Jun 25 03:54 main.py*
root@75167bd3c633:/usr/app#


Login to docker shell:

D:\Python_Docker\1_Python_Script_Docker>docker images
REPOSITORY     TAG       IMAGE ID       CREATED         SIZE
python_hello   latest    bbe4b526ef6e   5 minutes ago   155MB

D:\Python_Docker\1_Python_Script_Docker>docker container ls
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

D:\Python_Docker\1_Python_Script_Docker>

D:\Python_Docker\1_Python_Script_Docker>docker images
REPOSITORY     TAG       IMAGE ID       CREATED         SIZE
python_hello   latest    bbe4b526ef6e   8 minutes ago   155MB


Remove docker images:
D:\Python_Docker\1_Python_Script_Docker>docker rmi python_hello
Error response from daemon: conflict: unable to remove repository reference "python_hello" (must force) - container 4f4dc54a94fd is using its referenced image bbe4b526ef6e

D:\Python_Docker\1_Python_Script_Docker>docker rmi -f python_hello
Untagged: python_hello:latest
Deleted: sha256:bbe4b526ef6ed68adfdc7ba2ad9dafd97d5189164bd0af00decfe8d54d1b3d2e

D:\Python_Docker\1_Python_Script_Docker>docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

D:\Python_Docker\1_Python_Script_Docker>