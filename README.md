### hdp-5-HUE-installation


> Install prerequisites

```sh
# log as root
sudo su - root

# install packages
yum install -y ant
yum group -y install "Development Tools"
yum install -y libkrb5-dev libmysqlclient-dev ko
yum install -y libssl-dev libsasl2-dev libsasl2-modules-gssapi-mit ko
yum install -y libsqlite3-dev ko
yum install -y libtidy-0.99-0 libxml2-dev libxslt-dev ko
yum install -y maven
yum install -y libldap2-dev ko
yum install -y python-dev ko
yum install -y python-simplejson python-setuptools
```

> Download and install HUE

```sh
# download 
wget https://dl.dropboxusercontent.com/u/730827/hue/releases/3.8.1/hue-3.8.1.tgz

# unpack package
tar -xvzf hue-3.8.1.tgz

# install 
cd hue-3.8.1
sudo make install

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

![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_conf3.png | width=50)

![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_conf4.png | width=100)

![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_conf5.png | width=80)
