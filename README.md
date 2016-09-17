# ssh-config
> Generating a new SSH key: `$ ssh-keygen -t rsa -C "your_email@example.com"`


**Create this file in your ssh folder: `$ touch ~/.ssh/config`**
### Basic Connection Options
```shell
# command line
$ ssh -p 22000 user_name@dev.example.com
```
```config
# contents of ~/.ssh/config
Host dev
    HostName dev.example.com
    Port 22000
    User user_name
```
Use: `$ ssh dev`

### Configuring Shared Options
```config
Host hapollo
    HostName example.com
    Port 4567

Host wapollo
    HostName company.com

Host *apollo
    User apollo

Host *
    User diffdefault
```

### Multiple SSH Keys settings for different github account
```config
# Default GitHub
Host github.com
    HostName github.com
    User your_username
    IdentityFile ~/.ssh/id_rsa.pub

# Work GitHub
Host work.github.com
    HostName github.com
    User your_work_username
    IdentityFile ~/.ssh/id_rsa_work.pub
```
Use: 
```shell
$ git clone git@github.com:ORGNAME1/some_repository.git
$ git clone git@work.github.com:ORGNAME1/some_repository.git
```
> Note: cd to some_repository and modify git config:

> $ cd some_repository

> $ git config user.name "your_username"

> $ git config user.email "your_email@gmail.com" 

### Forward all local port 9906 traffic to port 3306 on the remote db.example.com server:
```shell
# command line
$ ssh -f -N -L 9906:127.0.0.1:3306 user_name@db.example.com
# -f puts ssh in background
# -N makes it not execute a remote command
```
```config
# contents of ~/.ssh/config
Host database
    HostName db.example.com
    LocalForward 9906 127.0.0.1:3306
    User user_name
```
Use: `$ ssh -f -N database`


