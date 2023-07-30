# Introduction & Acknowledgement

This is a short memo about how to set up a VPN server on a VM.
It is based on the brilliant tutorial available on [this link](https://www.cyberciti.biz/faq/ubuntu-20-04-lts-set-up-openvpn-server-in-5-minutes/). On pdf version extracted on July 23 in [available here](https://github.com/kisina/vpn/blob/main/Ubuntu%2020.04%20LTS%20Set%20Up%20OpenVPN%20Server%20In%205%20Minutes%20-%20nixCraft.pdf).
The original repo can be [found here](https://github.com/Nyr/openvpn-install).

# How to get a server for free?

You can get server for free at [Oracle Cloud](https://cloud.oracle.com) using the "Always free" dedicated to testing the services. It gives access to small machine that are enough for setting up a server.
More information on this video (in french): https://www.youtube.com/watch?v=23NboTdWMXs

# Install the VPN server

Update your system and laucnh the bash script from the linked mentioned in the introduction (check the latest version on the original repo).

# Install the VPN client

This depends on the OS, but for linux you could use an instruction like

```bash
sudo apt install openvpn
```

Next, copy desktop.ovpn as follows:
```bash
sudo cp linuxdesktop.ovpn /etc/openvpn/client.conf
```

Test connectivity from the CLI:
```bash
sudo openvpn --client --config /etc/openvpn/client.conf
```

Your Linux system will automatically connect when computer restart using openvpn script/service:
```bash
sudo systemctl start openvpn@client # <--- start client service
```

# Launch the client
