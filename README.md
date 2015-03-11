# project ora12asm

The starting point for this project was:  https://github.com/hajee/vagrant-centos-5.10-ora12-rac. I did concider forking this project but what I'm doing is radically different, although I do really like the way he has automated setting up a disc array!

Using the vagrant-centos-5.10-ora12-rac project and using this you can easily build a two node RAC cluster with ASM with much of the Oracle Service deployed via puppet. This degree of automation is undoubtly extremely impressive but a bit more than I current require.

As I want to understand the background infrastructure better, so I'm not going to use puppet i.e. once I have the base Centos 5.8 image up, with the 7disc x 4G storage array up (via rake ... which looks incredibly useful add-on to Vagrant), then I perform the oracle grid and database creation steps using runInstaller, asmca, dbaca ...

For more details regarding how this project works please see: http://wiki.ebabel.eu/index.php/Oracle_asm_standalone
