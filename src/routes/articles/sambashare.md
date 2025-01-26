---
title: Share drive or fold using Samba in Ubuntu
date: '2024-08-24'
---

1. Install samba
```bash
sudo apt install samba
```
2. Modify your config
```bash
sudo nano /etc/samba/smb.conf
```
3. Skip to the bottom and add this section:

[whateveryouwantyoursharetobenamed]
path = /path/to/your/share
available = yes
valid users = yourusername
read only = no
browsable = yes
public = no
writable = yes

Ctrl O to write, then Ctrl X to leave

4. Then, make an smb user:
```bash
sudo smbpasswd -a yourusername
```

5. Then restart samba:
```bash
sudo systemctl restart smbd
sudo systemctl restart nmbd
```

You can now access your share via \\servnameorIP\sharename on your network.