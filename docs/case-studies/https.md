# Implementing HTTPS on a Webserver

HTTPS is pretty important nowadays for a website to have. It adds security for the users and increase credibility for the website owner.

In this case study, I'll be explaining to you what I did during HTTPS implementation on a webserver.

## Requirements

- VM with public IP
- Almalinux OS
- Domain name
- Python

This case study was performed on a VM with public IP provided by Oracle Free Trial. I picked Almalinux for the VM OS because I'm familiar with the setup. More often than not they already have Python installed.

I just bought a cheap domain name not only for the sake of this case study, but I'll be using this domain name more in the future to host my portfolio. At least that's the plan.

## Implementation

### Provision a VM

For the case study, I don't need that much resources for the VM since I'll be hosting a light static page. Also it needs to have public IP since I want it to be accesible to the internet.

I choose Almalinux for the OS because, as I said earlier, I'm familiar with the setup. I don't want this study case to be another rabbit hole that needs days to finish, so I stick with something simple and don't complicate it.

I could've settled for the lowest resource, 'Always Free-eligible' shape with only 1 core OCPU & 1 GB memory, if not for the shape to be unavailable in the region that I picked. So I picked the one with 1 core OCPU and 15 GB memory. It's overkill I know, but that's the lowest I could get.

I also need to setup the networking. I created the bare minimum 'defaults' that can connect my VM to the internet. Mainly by checking the option to 'Automatically assign public IPv4 address'.

I also need to add SSH keys. Since I already have SSH keys that I often use, I choose the option to 'Upload public key file (.pub)' that is located on `~/.ssh/`.

### Server Hardening

Now that I got the VM running Almalinux, I need to SSH to the machine to do the tasks. The default username for CentOS family OS is `opc` and the public IP is provided in the Instance page in Oracle Cloud. If you can't connect to the VM, check in the networking section and make sure you checked the option to connect to the internet, or something like that. Ask me how I know that.

After I logged into the VM, I checked the common packages and surprised that there weren't any firewall package like `firewalld` or `ufw`. Apparently you have to go to the Security List in Networking section to edit the Security Rules. On the description listed:

> Instance traffic is controlled by firewall rules on each Instance in addition to this Security List

But before touching the firewall, I hardened the SSH. On the `/etc/ssh/sshd_config`, its mentioned that its better to keep the file unmodified to serve as the default value for future reference and create a `\*.conf` file under `/etc/ssh/sshd_config.d/`.

So, I created a file in `/etc/ssh/sshd_config.d/99-hardening.conf` with the value below:

```
PasswordAuthentication no
PermitRootLogin no
PubkeyAuthentication yes
```

Even when `PasswordAuthentication no` already listed on `/etc/ssh/sshd_config.d/50-cloud-init.conf`, `root` user unavailable, and `PubkeyAuthentication yes` already the default int `sshd_config`, I still put that as a security baselining.

The reason I didn't change the SSh port is because its a 'Security by Obscurity', which isn't a security. Well, it maybe is since it'll reduce the amount of bot trying to connect to the default SSH port. But that won't stop a targetted attack that scans the port before attacking.

After that, restart the `sshd` with `sudo systemctl restart sshd`.

### Firewall/Security List


