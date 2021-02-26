## How to make custom Debian-CD.iso:

### 1. Clone this repo to your  PC.

### 2. Modify files in *profiles* folder:
- x-basic.preseed ~ change users, passwords, time zone, partitions, RAID configuration etc.
- x-basic-packages ~ add extern packages to your installation  
- x-basic-postinst ~ post installation script

### 3. Run `$vagrant up`


After a while, your <debian-custum-image>.iso should appear. 