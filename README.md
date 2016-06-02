# nomachine-docker
Run NOMACHINE inside a Container

How to run NoMachine server v. 4 inside Docker
Given that Docker is installed on the host machine, to run NoMachine server inside Docker it's enough to build an image from the Dockerfile and launch it.

For example to build an image with MATE as desktop environment:

1) Create your image directory, e.g.

mkdir nomachine

2) Copy content of the Dockerfile below to: nomachine/Dockerfile.

Adapt the Dockerfile to your needs.

3) Copy content of the wrapper script below to: nomachine/nxserver.sh.

and set executable permissions:

chmod +x nomachine/nxserver.sh

4) Build the image:

docker build -t=nomachine nomachine

5) Run the container:

docker run -d -p 4000:4000  nomachine

Set a different port if necessary (see points d and e below).

You can specify multiple ports by reiterating the -p option, e.g.

docker run -d -p 4000:4000 -p 22:22

Dockerfile for NoMachine Workstation v. 4 for evaluation

The Dockerfile you have already downloaded the NoMachine package v. 4.

It uses the following NoMachine Workstation package for evaluation: nomachine-workstation-evaluation_4.6.22_2_amd64.deb and it is just an example that can be easily adapted to whichever other package you want to try.

a) Replace the name of the package with that of the server you intend to run. Note that a server wrapper script is always requested.

b) By default it will run a MATE desktop environment, you can adjust it by replacing 'mate-desktop-environment-core'  with the desktop of your choice.

c) It will create the nomachine user with nomachine as a password, you can specify a different username and password and repeat instructions for creating additional users.

d) The 'EXPOSE 4000' command opens port 4000, the default port for connections by NX protocol. Set 'EXPOSE 22' if you intend to use connections by SSH protocol. In this case modify the Dockerfile to install openssh-server.

e) Connections by the web use port 4080 and 4443 by default. Add 'EXPOSE 4080 4443' to let users run web sessions. This applies to NoMachine Cloud Server only.
