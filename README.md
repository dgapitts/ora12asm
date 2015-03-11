# project ora12asm

The starting point for this project was:  https://github.com/hajee/vagrant-centos-5.10-ora12-rac. I did concider forking this project but what I'm doing is radically different, although I do really like the way he has automated setting up a disc array!

Using the vagrant-centos-5.10-ora12-rac project and using this you can easily build a two node RAC cluster with ASM with much of the Oracle Service deployed via puppet. This degree of automation is undoubtly extremely impressive but a bit more than I current require.

As I want to understand the background infrastructure better, so I'm not going to use puppet i.e. once I have the base Centos 5.8 image up, with the 7disc x 4G storage array up (via rake ... which looks incredibly useful add-on to Vagrant), then I perform the oracle grid and database creation steps using runInstaller, asmca, dbaca ...

For more details regarding how this project works please see: http://wiki.ebabel.eu/index.php/oracle_asm_standalone

Please note that the oracle sofware (.zip and .rpm) must be downloaded from oracle.com:
```
~/projects/ora12asm $ ls *.zip *.rpm|sort
cx_Oracle-5.1.1-11g-py27-1.x86_64.rpm  << only exception ... this is available via http://sourceforge.net/projects/cx-oracle/files/5.1.1/
linuxamd64_12c_database_1of2.zip
linuxamd64_12c_database_2of2.zip
linuxamd64_12c_grid_1of2.zip
linuxamd64_12c_grid_2of2.zip
oracleasm-2.6.18-371.el5-2.0.5-1.el5.x86_64.rpm
oracleasm-support-2.1.8-1.el5.x86_64.rpm
oracleasmlib-2.0.4-1.el5.x86_64.rpm
redhat-release-6Server-1.noarch.rpm
```
as you must sign the Oracle EULA and them into the root of the project on the host (which is cross mounted as /vagrant). 
