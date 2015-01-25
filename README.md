resolve_files
=============
This script is hugely beneficial. 
use to create mirrored files systems on separate linux installations via go between nfs mounted file server

Requirements:

1) each system must be pre configured to nfs mount the file server, use mount, unmount and check status scripts to test
2) the hard_coded.src file needs to be created and edited to work for local user, create file by copying from hard_coded.src.template
3) a parameters file must be in place can be created from the template but is easier to create from an existing working copy

run syntax: sudo ./resolve_files # must be run with root privs
