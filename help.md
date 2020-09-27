#Aliases:
sudo nano ~/.bash_aliases >> add aliases:
*alias cls="clear"*

sudo nano ~/.bashrc >> uncomment: 
*if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi*

#Package Installation
*sudo dpkg -i package.deb* 
*sudo apt-get -f install*

#Adding Envierment Variables
sudo nano /etc/environment
JAVA_HOME="/usr/lib/jvm/open-jdk"
source /etc/environment
echo $JAVA_HOME

#Adding programs to console
*export PATH=$PATH:<pathtoadd>*
*source bashrc*

##Ading java for all users
sudo nano /etc/profiles.d/java.sh
PATH=$PATH:/path/to/ANT/bin
source /etc/profiles

##sudo removal
*sudo visudo -f /etc/sudoers.d/shutdown 
user host = (root) NOPASSWD: /sbin/shutdown
user host = (root) NOPASSWD: /sbin/reboot
%sudo   ALL=(ALL) NOPASSWD: /usr/sbin/service lightdm restart
Defaults insults*

#Scanning disk space
du -sh .* | sort -n
du -sch .[!.]* * |sort -h

## Fixing Screen Tearing
You then need to add the following line to the "Screen" section of the opened Xorg configuration file:
Option "metamodes" "nvidia-auto-select +0+0 { ForceCompositionPipeline = On }"
or use console: 
nvidia-settings --assign CurrentMetaMode='nvidia-auto-select +0+0 { ForceCompositionPipeline = On }'

#Nvidia
## blackisting nouveau and instatlling nvidia drivers
*sudo nano /etc/modprobe.d/disable-nouveau.conf

blacklist nouveau
options nouveau modeset=0
sudo update-initramfs -u
sudo reboot
sudo service mdm stop
sudo sh ./NVIDIA-Linux-x86_64-358.16.run
sudo service mdm start*

