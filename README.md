resolve_files
=============
This script is hugely beneficial. Used to create mirrored files systems on separate linux installations via go between nfs file server.

Requirements:

1) each system must be pre configured, able to nfs mount the file server, use mount, unmount and check status scripts to test
2) the hard_coded.src file needs to be created and edited to work for local user, create file by copying from hard_coded.src.template
3) a parameters file must be in place can be created from the template but is easier to create from an existing working copy
4) must be run as root or user with sudo root privileges

run syntax by non root user:

sudo ./resolve_files
