This script is capable of syncing files between a host and a remote server using the rsync service. 

Currently, this script will copy four different directories, and mirror them on a remote server. 

To run this script, download the file and place it in any directory. Open the file and edit the remote host username and address. 

Save the script and make the script executable by using the following command:

chmod 755 rsync_backup

This script can be automated by adding a cron job.

-u - This option skips copying files if they are newer on the server. If for some reason there was a newer file on the server than on the client machine, it would not be overwritten on the server.

-r - This option copies all files recursively.

-v - This option increases the verbosity that is output by the rsync program.

-e - This command followed by ssh tells rsync to copy the files over SSH. This option ensures security if files are being copied over the internet. In order to use this option successfully, SSH must be configured on the server. SSH without a password to the remote server must also be configured. A quick Google search should provide a tutorial on how to accomplish both those tasks. If files are being copied over a local network, this command really is not necessary.

--progress - This option shows the progress rsync is making during the copying process.

--delete - This option will delete files on the server if they are no longer on the client machine. This means that if a file is accidentally deleted on the client machine it will also be removed on the remote machine.

--chmod=D775 - This option gives each file the proper permissions for cloud hosting. If this option is taken out, folders within the cloud directories will not show up on the website.

/path/to/your/media/documents/* - This is the path to your documents folder. The /* at the end of the command ensures all files within the documents folder are transferred. Change the script to match the path to each of your media directories.

YOUR_SERVER_NAME@YOUR_DOMAIN NAME:~/public_html/documents/ - This command is the path to the server directory the files will be copied to. Replace YOUR_SERVER_NAME with the name of the remote server server. In the case of this guide, it would be server. Replace YOUR_DOMAIN_NAME with the domain name of the remote machine. Finally, replace /documents/ with the appropriate remote media folder.

--exclude=.htaccess --exclude=.htaccess~ - Because the --delete option is in place, these files could potentially be deleted off the server because they are not on the client machine. However, since these files protect the server, they should not be deleted. This command keeps them from being deleted.

To run the script, type:
./rsync_backup

If there you get a permission denied error type:
chmod 755 rsync_backup