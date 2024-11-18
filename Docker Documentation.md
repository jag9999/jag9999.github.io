
Firstly, I opened up my Kali Linux VM through Oracle VirtualBox, and updated and upgraded all the packages before continuing the installation

sudo apt update && sudo apt upgrade -y

After updating and upgrading all packages, I installed Docker

sudo apt install docker.io -y

I then installed docker compose 

sudo apt install docker-compose -y

I then created a new directory and cd'd into it, so that I can start with installing the required files 

mkdir docker-project
cd docker-project

Then, I nano'd into a docker-compose.yml file so that I could start with adding the content for the application I chose, which will be WordPress
![[docker wordpress nano 1.png]]

After filling out the proper information needed inside the yml file for the WordPress application, I saved the information that was documented into the file by doing Ctrl+o and then saving it and Ctrl+x to get out of the program

Considering that with this yml file I created, I am required to run every command with sudo permissions. Although this isn't necessarily a bad thing, I am choosing to add my user to the docker group.

sudo usermod -aG docker $USER

After adding the user to the group, I then verified that the tcp port was working with the docker container

sudo netstat -tuln | grep 8000

The number 8000 is the port that is binded to the specific application. This can vary based on what port number you choose. Run this command to confirm that your container is exposed properly to the port. You should receive an output showing the Transmission Control Protocol (TCP) and where its routed to. Reconfigure your port inside your .yml file if theres no output

After this, since I named the directory to be localhost in the contents of my yml file, I accessed my application through an http URL

http://localhost:8000/

When I type this URL into my local VM browser, it pulls up my chosen application, which is WordPress

![[WordPress Docker .png]]









