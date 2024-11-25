
This documentation will explain how I used DigitalOcean to install Wireguard with Docker

Firstly, I navigated to [DigitalOcean](https://www.digitalocean.com) and signed up for a new account with a URL that was given from the professor, which gives us $200 credit for 2 months of usage.

After this, I created a Ubuntu 24.04 Droplet and selected the $8/month option under the "Premium Intel" option.

When creating a password, I went ahead and selected password, although SSH would be the better option, as it provides more security.

After doing this, I then hit "Create", which creates the droplet.

I then used WSL, which is Windows Subsystem Linux. The Command prompt can work as well, as all you need to do after creating the droplet is to SSH into the root IP.

Since I am using WSL, I went ahead and SSH'd into my droplet 

ssh root@(IP GIVEN FROM DROPLET)

The IP used is the IPv4 IP, and then once prompted, I type "yes" to authenticate the key for the droplet establishment

After this happens, I re-ssh into the droplet, and type my password in.

After typing my password in, I get a "Welcome Ubuntu 22.04.4 LTS" message.

I then installed docker and docker-compose

sudo apt install docker
sudo apt install docker-compose

I then setup Wireguard in docker

mkdir wireguard
cd wireguard

I then made a docker-compose.yml file inside the wireguard directory

nano docker-compose.yml

Inside this docker file contains the needed contents for Wireguard. These contents can vary based on the version you install, but I chose to fulfill the yml file with the contents I will show below. When filling out your server URL, make sure you put your IP to your droplet.

![Wireguard compose contents](https://github.com/user-attachments/assets/84a596c8-bbed-4233-9e83-28187e8a5da0)


Once this was complete, I ran the docker container 

docker-compose up -d

Now, for connecting Wireguard to my PC, I used a secure copy to transfer the files to my local computer. This is to help transfer the files to my local PC. Make sure you transfer them from the directory you made for the Wireguard installation

Transferring files for the PC. I am choosing my Desktop folder

scp root@YOURIP:~/wireguard/config/peer1/peer1.conf ~/Desktop/peer1.conf

After running this command, I am then prompted again for authenticity, and I type yes, and then type in my password to the droplet

Once the config file appeared on my desktop, I then shared it to myself through email so that my phone can access the config file.

I then added the config file to the Wireguard app through my phone, were I was prompted to allow the config file, and then I was able to connect to the VPN.

![Allowing configuration phone](https://github.com/user-attachments/assets/e1136e0b-3ba7-443c-901d-0c15b4ab3411)

![Connection via phone](https://github.com/user-attachments/assets/c36d7dc9-bcb8-4a75-8239-458f187a7980)

Now, with connecting it to my PC, I installed Wireguard from the internet. Choose the version of Wireguard that is based on your Operating System. Since mine is Windows, I chose windows.

After installing Wireguard, I imported the tunnel with my config file and then clicked activate to activate the VPN. To show this worked, I will show the IP before and after.

![Before Wireguard IP](https://github.com/user-attachments/assets/78e4cfef-3a9b-4bb8-b04b-0a59f18f00ee)

![After Wireguard IP](https://github.com/user-attachments/assets/77b695a5-14ff-432a-b13f-7298e5f21d03)
