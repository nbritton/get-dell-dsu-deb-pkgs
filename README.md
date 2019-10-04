# get-dell-dsu-deb-pkgs
Retrieve Dell System Update .deb packages for Ubuntu Server.

For some asinine reason Dell does not have a Ubuntu package repository for the Dell System Update ("DSU") utility, they publish a .deb package, however it's hidden away inside of a Dell Update Package ("DUP") BIN file. This tool fixes that oversight by retrieving the .deb packages for you, and also creates a local DSU package repository that you can host yourself.

```bash
curl -s http://www.exabit.io/ubuntu/get-dell-dsu-deb-pkgs | bash;
```

```bash
echo "deb [arch=amd64 trusted=yes] http://yoursite.com/dsu/ /" > /etc/apt/sources.list.d/dsu.list;
```

Note: All DSU versions have a runtime dependency on libssh2-1, and DSU 1.7+ also requires libgpgme11.

```bash
apt update && apt-get -qq install dell-system-update libssh2-1 libgpgme11;
```

### Dell DSU .deb package list:
- dell-system-update_1.7.0-19.05.00_amd64.deb
- dell-system-update_1.6.0-18.11.00_amd64.deb
- dell-system-update_1.5.3-18.03.00_amd64.deb
- dell-system-update_1.5.2-18.01.00_amd64.deb
- dell-system-update_1.5.1-17.11.00_amd64.deb
- dell-system-update_1.5.0-17.08.00_amd64.deb
- dell-system-update_1.4.2-17.05.00_amd64.deb
- dell-system-update_1.4.1-17.04.00_amd64.deb
- dell-system-update_1.4.0-17.02.00_amd64.deb

To retrieve one of these packages individually, use the following command:

```bash
curl -s <BIN-FILE> | sed "0,/^#####Startofarchive#####/d" | tar --wildcards --no-anchored '*.deb' -zxf -;
```
### Dell DSU Linux BIN file list:
https://downloads.dell.com/FOLDER05605556M/1/Systems-Management_Application_DVHNP_LN64_1.7.0_A00.BIN
https://downloads.dell.com/FOLDER05327755M/1/Systems-Management_Application_FT56W_LN64_1.6.0_A00.BIN
https://downloads.dell.com/FOLDER04882835M/1/Systems-Management_Application_RT3W9_LN64_1.5.3_A00.BIN
https://downloads.dell.com/FOLDER04748790M/1/Systems-Management_Application_T50FD_LN64_1.5.2_A00.BIN
https://downloads.dell.com/FOLDER04752936M/1/Systems-Management_Application_4DXF8_LN64_1.5.1_A00.BIN
https://downloads.dell.com/FOLDER04496162M/1/Systems-Management_Application_YH0VX_LN64_1.5.0_A00.BIN
https://downloads.dell.com/FOLDER04327910M/1/Systems-Management_Application_0M81X_LN64_1.4.2_A00.BIN
https://downloads.dell.com/FOLDER04297923M/1/Systems-Management_Application_G41KN_LN64_1.4.1_A00.BIN
https://downloads.dell.com/FOLDER04166247M/1/Systems-Management_Application_YKMFW_LN64_1.4.0_A00.BIN
