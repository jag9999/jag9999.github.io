When installing ArchLinux, I took a torrent file and downloaded the torrent file. After doing this, I then installed qTorrent, which is a software that helps with taking torrent files and converting them into the actual file, which allows me to get the .iso image file needed to install Arch Linux to my Virtual Machine. On the other hand, if you do not want to go down the torrent route, you can always visit the download page and find the latest mirror file to download the .iso image.

Once this was complete, I then opened up oracle VM VirtualBox, and hit "New", which allows me to create a new VM. After doing this, I typed in "Arch Linux" as the name of the Virtual Machine, which defaults my operating system to Linux(64-bit). After doing this, I selected the iso image that was extracted from the torrent file. Then, I allowed 4024MB of ram, since that is half of my total allcoated ram my system can hold, and 5 core processors to improve speed of operating my VM. I selected "FInish", completing process of installing the iso-image to my Virtual Machine. Before I proceeded to the next step, which was to hit "start" and install ArchLinux, I then I confirmed all my settings were correct by right clicking and going through each module. These modules in the settings included

General
System
Display
Storage
Audio
Network
Serial Ports
USB
Shared Folders
User Interface

After confirming all of these modules were installed accurately within my systems standards, I mainly confirmed that the Network port was NAT and my storage controller IDE was the archlinux iso image. Then, as recommended, I edited the display video memory to be as max as possible, which provides the best display possible for the VM.

After checking with all the modules above, I then hit start and started up the Virtual Machine. It prompted me to a selection of OS's to launch from, and I selected the first one (Arch Linux x86_64).

Arch Linux then booted up into root@archiso ~ #:

Through this, I then decided to run the command "archinstall"

Archinstall prompts you to a small GUI with multiple kinds of options, including base-installation settings. Some of these options included

Archinstall language
Mirrors
Locales
Disk Configuration
Bootloader
Unified kernel images
Swap
Hostname
Root password
User account
Profile
Audio
Kernels
Additional packages
Network configuration
Timezone
Automatic Time Sync (NTP)
Optional Repositories

Through these options have certain subsections on what to select per option. For this process, I left the Archinstall language untouched, since the default language is English.

I left the mirrors option alone, as well as locales, since the keyboard layout and layout was English, and the encoding was set to UTF-8.

After looking at this, I went to Disk configuration. This step is important, because it involves partitioning the disk into two parts, one that involves the Bootup, and the other available space to be used for the installation.

Selecting disk configuration, it pulls up a GUI of 3 partitioning options. I selected the first one, which was "Use a best-effort default partition layout." I chose this because I did not want to mess up my installation by selecting the other options, which involve manually partitioning your disk.

After selecting "Use a best-effort default partition layout", it prompts open two disks. I selected the VBOX hard disk, which prompts up 4 options to select. Each option will determine which filesystem your main partition should use. I selected "ext4", because it provides larger file and volume support, as well as performance and backward compatibility.

Selecting this option and hitting enter then prompted me back to the original GUI to complete the rest of the installation. I left bootloader the same, as well as Unified kernel images and swap, because swap was already defaulted to 'True'. I went to root password, and defaulted the password to just be root. After this option, I selected "user account", which prompts you to adding a user and then confirming and exiting. I added three users, one including myself, then the other two being the instructors of the course, justin and codi. I made my own personal password for my user, and then used the password "GraceHopper1906". I made each user sudo users, including me, as this was the goal for the assignment.

After this, I was prompted back to the original GUI, and I created a Profile for my Arch Installation.

Selecting profile, I then selected type, which prompted me to 4 pre-programmed default_profiles. These profiles consisted of

Desktop
Minimal
Server
Xorg

For this particular installation, Desktop was the default_profile that was selected, as we are wanting to install a Desktop Environment (DE). This option prompted multiple choices, and I ended up choosing GNOME, as I felt my systems specs could handle this Desktop Environment. I also liked how the GUI looked, as selecting the Desktop Environment is mainly personal preference. This then prompted to review the type, Graphics driver, and Greeter. I chose to keep the default Greeter to be gdm. 

I then went back to the original GUI that was prompted to complete installation. I selected audio, which then gave me two options to select from

Pipewire and Pulseaudio

I chose Pulseaudio because Pulseaudio has been around for much longer than Pipewire, and I just felt that it would be best to stick to something that was more modern andn ot as new.

Once again, I was prompted to the original GUI, and then selected Network Configuration. I selected the "Use NetworkManager (necessary to configure internet graphically in GNOME and KDE)."

I felt this was the most appropriate option to select, since im using GNOME and it says its necessary to configure internet graphically.

Prompted back to the original GUI, I selected my appropriate timezone based on my current location, and then selected Install. Prompted back to the original cmd terminal, I hit enter, which resulted in the install to format onto my partitioned disk, and then I typed Y to proceed with the installation. This process to quite a bit, as there much to install, including the base-installation of Arch Linux, as well as the Desktop Environment (DE) I selected. 

Once installation was complete, I typed 'reboot' into the root@archiso ~ #: which rebooted my Virtual Machine. This prompted me back to the Original GUI, and then I selected "Boot existing OS." Selecting this, I hit "Arch Linux", which then prompted me to GNOME, my new Arch Linux Desktop Environment, which displayed the three sudousers I created prior to installation (one of those users including me). I logged in using my password, and was now logged into my new Arch Linux Desktop Environment (DE).

I opened the console and installed two different shells that were other than bash. I installed both zsh and fish.

To install zsh, I ran the command 

sudo pacman -S zsh

To get into zsh, I simply type 'zsh', and to confirm im actually in zsh, I type 'ps' in the console, which displays the current running processes. If zsh appears, it means zsh is currently running.

Alongisde installing fish, it is the same command, except we are putting "fish" at the end of our sudo pacman command

sudo pacman -S fish

Lastly, to get into fish, it is the same exact processing as if I was to want to enter into zsh. You would type 'fish', and then if you want to confirm you're in fish, you would type ps to see the current running processes. With fish, it is very obvious if you are in this shell, as it has specific coloration and looks more distinct than other shells.

Next, we are needing to install SSH. SSH is secure shell, which is a network protocol that allows two computers to communicate over an unsecured network, but securely. Helps with remote access, tunneling, and File Transfer.

To install SSH, you type the command 

sudo pacman -S openssh

To prompt the sudousers justin and codi to be required to change their passwords after entering their password given to them, I ran two commands, basically the same command but for each user.

sudo chage -d 0 justin
sudo chage -d 0 codi

after this, I ran another command to open up the sudoers

sudo visudo

then, I went into the file to locate the following line:

%wheel ALL=(ALL:ALL) ALL

After uncommenting it, I ctrl + O to save my changes, then ctrl + X to exit the file.

To create aliases for bash and zsh (specifically .bashrc and .zshrc), I nano'd into each file and typed
alias ll='ls -lah'
alias update='sudo pacman -Syu'

and saved both files in nano by Ctrl + O, and exited each file by doing ctrl + X

Lastly, I typed 

source ~/.bashrc 
and
source ~/.zshrc

This saves my current changes to each file.

When it comes to changing the color fonts to the terminal, I changed the look of my username in bash and defined it to look

Green for my username
Blue for my working directory

by changing the value commented in the PS1 value

PS1='\[\e[1;32m\]\u@\h:\[\e[1;34m\]\w$\[\e[0m\] '

For the zsh shell, I installed Oh My Zsh. I liked the design and how it changed the terminal theme. To do this, I opened the .zshrc file by doing 

nano ~/.zshrc

Once I opened this file, I typed

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

After typing this into the file, I Ctrl + O to save the file, then Ctrl + X to exit the file.

I wanted to change the theme to a different choice, so after I made these changes then ran source ~./zshrc to save the changes.

After saving these changes, I nano'd back into the file and scrolled until I found the line

ZSH_THEME

I changed the theme inside the quotations to a different them, specifically "agnoster". After googling this theme, I thought it would make the zsh shell look cleaner.

After changing these settings, I went into terminal and changed the way it looked by going to preferences, and then changed the background color to be black and my font to be cyan. This completely negates the change I made to my original bash shell, which is okay, but I can always go back to the regular look by not selecting the profile I made for the terminal apperance.




