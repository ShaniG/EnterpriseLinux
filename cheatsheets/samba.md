#Samba
Below you can find the cheats for a samba server RHEL7.
Also a checklist for troubleshooting the server.
##Cheats
###Installation
* `libsemanage-python`
* `samba-common`
* `samba`
* `samba-client`

###Firewall
* `firewall-cmd [--zone=<zone>] --add-service=samba [--timeout=<seconds>]` samba service add to firewall

###Samba & Selinux
* `vi /etc/samba/smb.conf` samba configuration file ( all settings )
* `chcon -R -t public_content_rw_t /path/to/dir` change permission.
* Selinux settings:
  * `setsebool -P samba_export_all_rw 1`
  * `setsebool -P allow_smbd_anon_write`
  * `setsebool -P allow_httpd_anon_write 1`
  * `setsebool -P samba_enable_home_dirs 1`
* `systemctl restart smb.service` restart smb service

##Checklist
1. Check all physical components ( wiring,...)
2. Check if packages are installed (above: cheats/installation)
3. Check if the services are running : `systemctl status smb.service`
4. Check firewall: `systemctl status firewalld, firewall-cmd --state, firewall-cmd --list-all/--list-services`
5. Check users existence: `cat /etc/passwd or id [id/username]`
6. Check groups: `cat /etc/groups`
6. Check configuration file: `cat /etc/samba/smb.conf`
7. Check Selinux booleans: `getsebool -a | grep [samba_export_all_ro,samba_export_all_rw,samba_anon_write,samba_enable_home_dirs]`
8. Check permissions: `ls -l`

**Tools:** 
dddd
