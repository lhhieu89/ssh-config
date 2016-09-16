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


