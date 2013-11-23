A Vim Plugin to sftp sync and run command remotely
============

This plugin can help you to sync code file with remote server, and run shell script of remote server in vim locally, no ftp needed, because it run with sftp.

After you modify a local file and save, the plugin will upload the file, overwrite the file of same namein the corresponding folder automatically. And of course, it also can download the latest release code file in the remote server if you want to. 

If you have some shell script in the remote server needed to run to deploy the project, just configure it in .vimrc, and type "\run" in vim, it will be done.

Part of the plugin is written in Python, and worked well on Windows(Local machine is Windows, and the remote server is linux).

Installation
----
You must have vim compiled with +python support. You can check that using the command:

    vim --version | grep +python

and then installed paramiko module
Reference:http://referhere.blogspot.com/2011/11/how-to-install-paramiko-on-windows.html

The last, install this plugin using [vundle],[pathogen] or your favorite Vim package manager.
or just throw it in plugin folder

Usage
----
    <leader>su
    Upload the file
    
    <leader>sd
    Download the file

    <leader>run
    run the shell script

Description
----
Please write config in .vimrc file following like.
    let g:vim_sftp_configs = {
    \      'sample_server_1' : {
    \       'upload_on_save'   : 1,
    \       'download_on_open' : 0,
    \       'confirm_downloads': 0,
    \       'confirm_uploads'  : 0,
    \       'local_base_path'  : 'E:\Projects\src',
    \       'local_base_path_regex'  : 'E:.Projects.src',
    \       'remote_base_path' : '/data/qspace/src',
    \       'command' : '/home/qspace/src/online.sh -param',
    \       'user' : 'root',
    \       'pass' : 'pass',
    \       'host' : 'xxx.xxx.xxx.xxx',
    \       'port' : '36000'
    \   }
    \}

sample1
 > Edit file : E:\Projects\src\file.php  
 > Sync to : /data/qspace/src/file.php
