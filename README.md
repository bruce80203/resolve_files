resolve_files
=============
Used to create mirrored directory structures on separate file systems.
Resolve_files is a bash shell script which I use to share files with my networked attached storage system (NAS).
Runs on the local system, the client side, to pull and push files to the nfs mounted NAS.

requires
=============
Local system must be able to execute a bash shell script (resolve_files).
Local system must be NFS mount capable prior to running the script.
Script uses the linux mount command, mount_diskstation and umount_diskstation are scripts to test the mount capability.
Must run as root, watch out this script can be dangerous and wipe out your file system if you are not careful!
I run with sudo:
sudo ./resolve_files

What it does:
=============
1) Ping NAS, if we can't ping, NAS exits with error message.
2) Opens up the parameter file. User can change mapped settings on each system here. The copy or non main side will become a mirror of the other side.
3) Mount NAS.
4) Compare function creates local list, checks for existence of each file on the mounted system and copies or deletes missing files. Timestamps of existing files are checked, new files replace older files.
5) Compare function is run again in reverse comparing NAS with local files. Steps 4 and 5 run in a loop, once for each area mapped.
6) Unmount the NAS, return count and time stamp.
