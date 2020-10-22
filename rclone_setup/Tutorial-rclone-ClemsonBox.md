## Tutorial to Use rclone tool 

## Introduction
This is the tutorial to use rclone to download data from your Cloud Storage to your remote machine(Using Clemson Box  and Palmetto for example)

## Requirements
1. Box account in Clemson 
2. a tool called **rclone** in your **remote machine** (Clemson Palmetto)
3. rclone in your **local machine** 

## Steps
1. **In your remote machine (Palmetto)**
    + add module of rclone
    ~~~bash
        module add rclone/1.51.0-gcc
    ~~~
    + Configure rclone  (link rclone to your Cloud Storage)
    ~~~ bash
        rclone config
    ~~~
     It will ask you to fill something in your terminal, you can just fill those like this 
     ~~~
        $ rclone config
        Current remotes:

        Name                 Type
        ====                 ====

        e) Edit existing remote
        n) New remote
        d) Delete remote
        r) Rename remote
        c) Copy remote
        s) Set configuration password
        q) Quit config
        e/n/d/r/c/s/q> n        # type n here to create new remote

        name> ClemsonBox    # Type the name you want of your driver. I choose ClemsonBox here
        Type of storage to configure.
        Enter a string value. Press Enter for the default ("").
        Choose a number from below, or type in your own value
        1 / 1Fichier
        \ "fichier"
        2 / Alias for an existing remote
        \ "alias"
        3 / Amazon Drive
        \ "amazon cloud drive"
        4 / Amazon S3 Compliant Storage Provider (AWS, Alibaba, Ceph, Digital Ocean, Dreamhost, IBM COS, Minio, etc)
        \ "s3"
        5 / Backblaze B2
        \ "b2"
        6 / Box
        \ "box"
        7 / Cache a remote
        \ "cache"
        8 / Citrix Sharefile
        \ "sharefile"
        9 / Dropbox
        \ "dropbox"
        ...
        Storage> 6          #Type 6 here to select the Box Cloud Storage


        ** See help for box backend at: https://rclone.org/box/ **

        Box App Client Id.
        Leave blank normally.
        Enter a string value. Press Enter for the default ("").
        client_id>          # Leave it blank
        Box App Client Secret
        Leave blank normally.
        Enter a string value. Press Enter for the default ("").
        client_secret>      # Leave it blank
        Box App config.json location
        Leave blank normally.
        Enter a string value. Press Enter for the default ("").
        box_config_file>    # Leave it blank


        Enter a string value. Press Enter for the default ("user").
        Choose a number from below, or type in your own value
        1 / Rclone should act on behalf of a user
        \ "user"
        2 / Rclone should act on behalf of a service account
        \ "enterprise"
        box_sub_type>       # Leave it blank to choose "user" as default
        Edit advanced config? (y/n)
        y) Yes
        n) No (default)
        y/n> n              # Leave it blank or  input "n", we don't need advanced config
        Remote config
    ~~~

    One Thing to note is that we need to choose **NO** for this question, since we can not open browser in remote machine (palmetto) to authorize rclone to access your cloud storage (Clemson Box)

    ~~~

        Use auto config?
        * Say Y if not sure
        * Say N if you are working on a remote or headless machine
        y) Yes (default)
        n) No
        y/n> n              # We need to choose "n" here, since we can not open browser in remote machine (Palmetto) 

        For this to work, you will need rclone available on a machine that has a web browser available.
        Execute the following on your machine (same rclone version recommended) :
                rclone authorize "box"
        Then paste the result below:
        result> 
     ~~~

     We need the token to fill to the "result>". We can get the token in your local machine. Please follow step 2 to get token here.


2. **In your local machine (your laptop)**
    + Link to download rclone to your local machine:
    https://rclone.org/downloads/

    + Open terminal in the directory of your rclone and run rclone you downloaded:
    ~~~
        rclone authorize "box"
    ~~~
    + Authorize rclone to access your Clemson Box by logining into your clemson account.  One thing to Note is that when authorizing your Clemson Box, you need to login your clemsonbox in a pop-up window. The account is **xxxx@clemson.edu**, no "g." and the password is your clemson account password

    + Copy the tokens shown up in the terminal in your local machine back to your rclone in your remote machine (Palmetto). The token will be something like this
    ~~~
    $ ./rclone.exe authorize "box"
    If your browser doesn't open automatically go to the following link: http://127.0.0.1:53682/auth?state=6r8wJLXIi6dkMSigvAfPNw
    Log in and authorize rclone for access
    Waiting for code...
    Got code
    Paste the following into your remote machine --->
    {"access_token":"T9xxxxxxxxxxTN","token_type":"bearer","refresh_token":"0xxxxxxxxxxxxxxxxu","expiry":"2020-10-22T13:35:43.3509811-04:00"}
    <---End paste
    ~~~


    Copy Your token, something like this,  back to  your remote machine
    ~~~
    {"access_token":"T9xxxxxxxxxxTN","token_type":"bearer","refresh_token":"0xxxxxxxxxxxxxxxxu","expiry":"2020-10-22T13:35:43.3509811-04:00"}
    ~~~


3. Check if the driver has been set up correctly in your remote machine:
    After you copy the token to your remote machine, it will pop up something like this. jus t type "y"  to finish. You will see a list of Current remotes in your terminal. Then you can exit the setup of your Cloud Storage in rclone
    ~~~
    -----
    y) Yes this is OK (default)
    e) Edit this remote
    d) Delete this remote
    y/e/d> y
    ~~~



## Usage
1. ls all files in cloud storage:
    ~~~
        rclone ls ClemsonBox:
        # ClemsonBox is the name you set when configuring rclone
        # path after  ClemsonBox: is the path you want to list
    ~~~

2. Copy files to current directory:

    ~~~
        rclone copy ClemsonBox:directory/   ./
    ~~~
    Different from linux commands, this copy all file/folders in "directory" to local path "./ "  We can not use "directory/* " to copy all files in rclone

3. Other Usage:
    Please Check the reference

## Reference
[1] https://rclone.org/googlecloudstorage/

[2] [Usage of rclone](https://rclone.org/docs/)

