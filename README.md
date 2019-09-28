# get-dell-dsu-deb-pkgs
Retrieve Dell System Update .deb packages for Ubuntu.

For some asinine reason Dell does not have a Ubuntu package repository for the Dell System Update ("DSU") utility, they publish a .deb package, however it's hidden away inside of a Dell Update Package ("DUP"). This tool fixes that oversight by retrieving the .deb packages for you and creates a local DSU package repository that you can host yourself.

```bash
curl -s http://www.exabit.io/ubuntu/get-dell-dsu-deb-pkgs.sh | bash;
```

```bash
echo "deb [arch=amd64 trusted=yes] http://www.example.com/dsu/ /" > /etc/apt/sources.list.d/dell-system-update.list
```
