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

> Configuring Hadoop
Configure Hadoop cluster to accept connections from HUE:
- ensure WebHDFS is enabled
![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_web_hdfs.png)
- proxy user hosts and groups for HUE
![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_proxy.png)
- enable HDFS file access control lists (FACLs) (optional)
![MetaStore remote database](https://github.com/gamboabdoulraoufou/hdp-5-HUE-installation/blob/master/img/hue_acl.png)



and add our cluster information to the HUE configuration file

