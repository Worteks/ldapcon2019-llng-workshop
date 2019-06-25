# LemonLDAP::NG Workshop

Workshop on [LemonLDAP::NG](https://lemonldap-ng.org/) for [Pass the SALT 2019](https://2019.pass-the-salt.org/).

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

After starting the image, you should be able to log in with : root / password

### LDAP server

OpenLDAP LTB server is already installed, you can check the service status:
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
