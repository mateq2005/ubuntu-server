# vsFTPd

### Installing vsftpd

```
sudo apt-get update
sudo apt-get install vsftpd -y
```

```
systemctl start vsftpd
systemctl enable vsftpd
systemctl status vsftpd
```

```
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.orig
```

### Configuring FTP Access

```
sudo nano /etc/vsftpd.conf
```

### Banner
```
ftpd_banner= Welcome to vsftpd.service
```

### Anonymous Connection

```
anonymous_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_root=/srv/ftp/anonymous
anon_other_write_enable=YES
```

```
sudo mkdir /srv/ftp/anonymous
sudo chown -R nobody:nogroup /srv/ftp/anonymous
sudo chmod -R 755 /srv/ftp/anonymous
```

### Users' Isolation

```
chroot_local_user=YES
chroot_list_enable=NO
allow_writable_chroot=YES
```

### Specific User's Isolation

```
chroot_local_user=NO
chroot_list_enable=YES 
allow_writable_chroot=YES
chroot_list_file=/etc/vsftpd.chroot_list
```
• add isolated user to *vsftpd.chroot_list*

### Specific User's not isolating

```
chroot_local_user=YES
chroot_list_enable=NO
allow_writable_chroot=YES
chroot_list_file=/etc/vsftpd.chroot_list
```
• add not-isolated user to *vsftpd.chroot_list*

### Restarting vsftpd

```
sudo systemctl restart vsftpd
```

**ftp://your_server_ip**

*tested*
