### hdp-5-HUE-installation


> Install prerequisites

```sh
# log as root
sudo su - root

# install packages
 yum -y install libffi-devel gmp-devel ant gcc gcc-c++ rsync krb5-devel openssl-devel \
 cyrus-sasl-devel cyrus-sasl-gssapi sqlite-devel openldap-devel libtidy libxml2-devel \
 libxslt-devel maven
 
 yum -y install mysql-devel mysql
 
 yum -y install python-devel python-simplejson python-setuptools
```

> Download and install HUE

```sh
# download 
wget http://gethue.com/downloads/releases/4.0.1/hue-4.0.1.tgz

# unpack package
tar -xzvf hue-4.0.1.tgz

# create hue directory
mkdir -p /usr/local/hue

# Copy untar binaries into the new folder
mv hue-4.0.0/* /usr/local/hue

# go to hue directory
cd /usr/local/hue

# Build the hue module
make apps


```

> Configure Hadoop cluster to accept connections from HUE:
- ensure WebHDFS is enabled
![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_web_hdfs2.png)
- proxy user hosts and groups for HUE
![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_proxy.png)
- enable HDFS file access control lists (FACLs) (optional)
![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_acl.png)


> Add cluster information to the HUE configuration file

```sh
# create new copy of HUE config file
cp /usr/local/hue/desktop/conf/hue.ini /usr/local/hue/desktop/conf/hue.ini.bkp

# edit HUE configuration file
vi /usr/local/hue/desktop/conf/hue.ini

# make change according to the following step, save and quit

```

![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_conf1.png)

![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_conf2.png)

![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_conf3.png)

![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_conf4.png)

![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_conf5.png)

> Start HUE

```sh
# add user HUE
adduser hue

# set hue password
passwd hue

# set permission to hue user
chown -R hue:hue /usr/local/hue

# go to HUE folder
cd /usr/local/hue/build/env/bin/

# run HUE
./supervisor

```

> Configure HUE to start after reboot
```sh
# edit crontab as root
crontab -e 

# add the following line
#### START ####
#start HUE
@reboot sleep 120; /usr/local/hue/build/env/bin/supervisor -d
#### END ####

```

> Go to http://IP:8888 or http:hostname:8888



