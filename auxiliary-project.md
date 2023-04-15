## In this project, we will be onboarding 20 new Linux users onto a server. We'll do this by creating a shell script that reads a ***name.csv*** file that contains the first name of the users to be onboarded.

### This script will:

1. read a **.csv** file that contains 20 new Linux users

2. create each user on the server, and add to an existing group called ***developers***. The developers group will be manually created.

3. will first check for the existence of the user on the system, before it will attempt to create the user.

4. The user that is being created also has a default home folder.

5. Each user has a **.ssh** folder within its ***HOME*** folder. If it does not exist, then we create it.

6. will create an **authorized_keys** file for each user’s SSH configuration 

7. The public key of the current user.

8. Before Deploying our script, we will need to update our current user with the correct public key and private key.

## **The Public Key**
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCzKZyicHxIkklSrNlxsJyyTrcIdBIt84Z0cQb3R4k0jH53kxkaT5hP8tfWTe62LXi7vV86fY+SX7TBNM76XGCbw/6vrMGegm6J1x2i1AiLNwq5nqTjOGn0AIwku4IlCCLAB7tdfRyVuCarmBlwny3lzRyybIUAWXR/D6vpN09MsDILbKdhay+Q/p9OUBMSLPqXdY/QIh/Oe3rVv1lwY3AohNfq7V3tO88zKswfA5iiexNiSYX1myT0OrX8cBE771j9quoNZhQgaLI1mIMtAvnHQChrn9k2nUaO/BMBCQGol5XzGv1ado7hgoVPoluIUD+FGNo/pH4zcmDLICH6drXY/C9MESnkMUPLFxBXKO/OitApY71vRao9nAhAwpVMsy6FqiOb5uawhvhoHYIHTV/f4EtagVagRMP2PxYMYR6jykIV4MPJTkCm+lGhTyMlRu+qRQjdLn8AAtHf4aEV8dIkoGh088DI7eA/4o0wz4OV4upH5ewSFS+5IHmRECEW5Nc=
```

## **The Private Key**
```
-----BEGIN OPENSSH PRIVATE KEY-----
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
kmaSGj362OnCCNAAAACWRhcmVARGFyZQE=
-----END OPENSSH PRIVATE KEY-----
```
<br>

### First we populate the [onboarding-users.sh](https://github.com/JenniferUgo/Auxillary-Projects-ShellScripting/blob/8a27ccc41a8f400de53146646d9c0ca401661788/onboarding-users.sh) with the shell script

<br>



### Then we copy our script named **onboarding-users.sh** into the directory of our instance using this command:
>`scp -i <name>-ec2.pem onboarding-users.sh ubuntu@<IP-address>:/tmp/`

### Then we connect to our instance using ths command:
>`ssh -i <name>-ec2.pem ubuntu@<IP-address>`

### Next, we create the project folder called **shell**
>`mkdir shell`

### Move into the **Shell** directory:
>`cd shell`

### Next, we move our script ***onboarding-users.sh*** from the current directory to the ***Shell*** directory, using this command:
>` mv /tmp/onboarding-users.sh /home/ubuntu/shell`

### Then we create the **names.csv** file, the public key (**id_rsa.pub**)file and the private key (**id_rsa**) file inside the ***Shell*** directory using this command:
>` touch names.csv id_rsa.pub id_rsa`

### We then open the **names.csv** file, with:
>`vi names.csv`
#### And populate it with random names, on each line.

### We also open the **id_rsa.pub** and **id_rsa** files and paste the public key and private key into them respectively.

### Next, we create the developers group, using this command:

>`sudo groupadd developers`
### Then we open the **onboard-users.sh** script and edit the public key file path. We replace `root/onboarding-users.sh/id_rsa.pub` with `/home/ubuntu/Shell/id_rsa.pub`

### We set permission on the sript so it can be executable:
>`sudo chmod +x onboarding-users.sh`
### To run the script, we first change to root user as we will not be able to execute the script as a normal user:
>`sudo su`

### After this we run our script
>`./onboarding-users.sh`

#### If there are no errors, this script has successfully onboarded 20 users to the Linux server and created a home directory, an .ssh folder and copied the public key into the *authorized_key* file of the users.
<br>

#### Check to see if the users are actually created:
>`tail -20 /etc/passwd`

### To check if we have successfully onboarded the users, we try and connect to the server randomly using any of the users.

### We open another terminal, cd into downloads.
>`cd downloads`
### Create a private key file and copy the private key into the file.
>`touch aux-project.pem`
### Next, we change permission of the new private key, using:
>`chmod 600 <new-private-key-file>`

### We can now connect by running the command.
>`ssh -i <new-private-key> <user>@<IP-address>`

### When it is connected, we can check for the home directory
>`ls -latr /home/`
### This displays the home directories of the users on the server.

### Then we cd into .ssh directory
>` cd .ssh`

#### Then list the content of the directory using `ls`.

#### This displays the *authorized_keys* file.

#### We can also connect randomly using any of the users.

#### Make sure not to give these new users sudo privileges so as not to mess up our server. The users' access to the server is limited.

### To watch the onboarding video [click here](https://drive.google.com/file/d/1H-xCmJAv4YX6K8vSbAgrC4ORbo9wrUpb/view?usp=drivesdk)

