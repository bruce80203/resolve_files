resolve_files
=============
This script is hugely beneficial. Used to create mirrored files systems on separate linux installations via go between nfs file server.

I'll try to explain as best I can through an example

My Windows laptop has the following directory structures:

/Users/Bruce/Documents
/Users/Bruce/Pictures
/Users/Bruce/Music
/Users/Bruce/Videos

Linux Mint which I boot through usb has similar directories:

/home/bruce/Documents
/home/bruce/Pictures
/home/bruce/Music
/home/bruce/Videos

also a couple more I want backed up:

/home/bruce/perl
/home/bruce/sql
/home/bruce/scripts

created directories on network files server:

/volumeA/Documents
/volumeA/Pictures
/volumeA/Music
/volumeA/Videos
/volumeA/perl
/volumeA/sql
/volumeA/scripts

here is my parameters file for the dual mount system

/Users/Bruce/Documents|/volumeA/Documents|main 
/Users/Bruce/Pictures|/volumeA/Pictures|main   
/Users/Bruce/Music|/volumeA/Music|main
/Users/Bruce/Videos|/volumeA/Videos|main       
/home/bruce/Documents|/volumeA/Documents|copy  
/home/bruce/Pictures|/volumeA/Pictures|copy    
/home/bruce/Music|/volumeA/Music|copy          
/home/bruce/Videos|/volumeA/Videos|copy
/home/bruce/perl|/volumeA/perl|main            
/home/bruce/sql|/volumeA/sql|main
/home/bruce/scripts|/volumeA/scripts|main

syntax of paramters file: local location|mounted location|main or copy
main field is defined when you decide to share OUT, all other systems should define this area as 'copy' with the intention of creating a mirrored copy from file server
how our Documents folder was shared in the above example: Windows > mounted file system > Linux Mint

here is an example of the parameters file on my Raspberry Pi:

/home/pi/perl|/volumeA/perl|copy
/home/pi/sql|/volumeA/sql|copy
/home/pi/scripts|/volumeA/scripts|copy         

Requirements:

1) Each system must be pre configured, able to nfs mount the file server. You can use the mount, unmount and check status scripts to test
2) The hard_coded.src file needs to be created and edited to work for local user, create file by copying from hard_coded.src.template
3) A parameters file must be in place which can be created from the template but is easier to create from an existing copy or above examples: <hostname>.chk_dirs.param
4) script must be run as root or user with sudo privileges

sudo ./resolve_files
