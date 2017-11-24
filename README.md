# Zeppelin-Webapp

> This is a modified version of zeppelin-web-0.7.2, mainly for the changes to the page permissions to support the Report can be embedded into other systems.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Please go to [install](http://zeppelin.apache.org/docs/snapshot/install/install.html) to install Apache Zeppelin from binary package.

### Installing

A step by step series of examples that tell you have to get a development env running

Git Clone Project
```
git clone http://git.dataw.com.cn/dmp/zeppelin-webapp.git
```

Cp Project

```
rsync -avhP ./zeppelin-webapp/* ${ZEPPELIN_HOME}/webapps/webapp/
```

Edit Shiro.ini

```
vim ${ZEPPELIN_HOME}/conf/shiro.ini
# Add the following
[urls]
/#/notebook/** = anon
/** = anon
```

## Running the tests

Starting Apache Zeppelin from the Command Line
```
${ZEPPELIN_HOME}/bin/zeppelin-daemon.sh start
```

### Add Zeppelin Service to Service Manager

> For Centos 7.0+

Add The Tollowing To The '/usr/lib/systemd/system/zeppelin.service' And Chmod 754

```
[Unit]  
Description=Zeppelin - a web-based notebook that enables interactive data analytics. You can make beautiful data-driven, interactive and collaborative documents with SQL, Scala and more. 
After=network.target remote-fs.target nss-lookup.target  
   
[Service]  
Type=forking  
ExecStart=/opt/zeppelin/bin/zeppelin-daemon.sh start
ExecReload=/opt/zeppelin/bin/zeppelin-daemon.sh restart
ExecStop=/opt/zeppelin/bin/zeppelin-daemon.sh stop
PrivateTmp=true  
   
[Install]  
WantedBy=multi-user.target  
```

Add Zeppelin Service To Systemctl

```
systemctl enable zeppelin.service
```

Start Zeppelin Service

```
systemctl start zeppelin.service
```

## Deployment

You can fork the project for further development

## Versioning

For the versions available, see the [tags on this repository](http://git.dataw.com.cn/dmp/zeppelin-webapp/). 

## Authors

* **Lonly** - *Initial work* - [Lonly](https://github.com/lonly197)

See also the list of [contributors](http://git.dataw.com.cn/dmp/zeppelin-webapp/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
