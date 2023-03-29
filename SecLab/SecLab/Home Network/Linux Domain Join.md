https://lanedirt.tech/2021/11/how-to-join-a-ubuntu-20-04-machine-to-a-windows-ad-domain/



Edit /etc/krb5.conf

```
[libdefaults]
default_realm = EXAMPLE.COM
rdns = false
```

THis resolves domain join error

sudo apt install -y realmd libnss-sss libpam-sss sssd sssd-tools adcli samba-common-bin oddjob oddjob-mkhomedir packagekit

sudo hostnamectl set-hostname ubuntu.ad.mycompany

sudo systemctl disable systemd-resolved.service

sudo systemctl stop systemd-resolved.service

Edit /etc/resolv.conf and add domain controller

realm discover asgard.local

sudo realm join -U Administrator asgard.local

sudo nano /usr/share/pam-configs/mkhomedir

	Add this:
	Default: yes
	Priority: 900

Delete:
	Session-Interactive-Only: yes

sudo pam-auth-update
	Add creat home dir on login

sudo systemctl restart sssd