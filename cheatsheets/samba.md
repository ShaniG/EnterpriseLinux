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
