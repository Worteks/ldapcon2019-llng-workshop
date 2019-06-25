# LemonLDAP::NG Workshop

Workshop on [LemonLDAP::NG](https://lemonldap-ng.org/) for [Pass the SALT 2019](https://2019.pass-the-salt.org/).

![LL::NG logo](images/logo_llng_600px.png "LemonLDAP::NG")

Goals:
* Install LemonLDAP::NG
* Configure authentication to OpenLDAP
* Protect sample applications with Handler
* Enable 2FA

Prerequisites:
* Virtualization system (like VirtualBox)
* Possibility to edit hosts file or a local DNS system
* Internet access

## Virtual image and first checks

Download the virtual image from this repository and import it.

After starting the image, you should be able to log in on console with : root / password

To log with SSH, use : worteks / password and then:
```
su -
```

Check which IP address was associated to your virtual machine. We will use the variable `VM_IP` in this documentation, you need to replace it by the IP of your own virtual machine.

### LDAP server

[OpenLDAP LTB](https://ltb-project.org/documentation/openldap-deb) server is already installed, you can check the service status:
```
systemctl status slapd
```

Access to configuration:
```
ldapvi -Y EXTERNAL -h ldapi:/// -b cn=config
```

Access to data:
```
ldapvi -Y EXTERNAL -h ldapi:/// -b dc=worteks,dc=com
```

### LDAP browser

[Fusion Directory](https://www.fusiondirectory.org/) is already installed, you can access it on http://`VM_IP`/fusiondirectory/.

You should see the following screen:

![FD login](images/screenshot_fd_login.png "Fusion Directory login page")

Log in with: fd-admin / password

You should see the following screen:

![FD home](images/screenshot_fd_home.png "Fusion Directory home page")

:exclamation: Now you are on your own. Follow the following steps and try to achieve all points!

## LemonLDAP::NG installation

:information_source: See also [official documentation](https://lemonldap-ng.org/documentation/latest/installdeb).

Use official repository:
```
vi /etc/apt/sources.list.d/lemonldap-ng.list
```
```
# LemonLDAP::NG repository
deb     https://lemonldap-ng.org/deb 2.0 main
deb-src https://lemonldap-ng.org/deb 2.0 main
```

Get GPG key:
```
wget -O - https://lemonldap-ng.org/_media/rpm-gpg-key-ow2 | apt-key add -
```

Update:
```
apt update
```

Install main package with Apache mod_perl:
```
apt install libapache2-mod-perl2 lemonldap-ng
```
