# Introduction & Acknowledgement

This is a short memo about how to set up a VPN server on a VM.
It is based on the brilliant tutorial available on [this link](https://www.cyberciti.biz/faq/ubuntu-20-04-lts-set-up-openvpn-server-in-5-minutes/). On pdf version extracted on July 23 in [available here](https://github.com/kisina/vpn/blob/main/Ubuntu%2020.04%20LTS%20Set%20Up%20OpenVPN%20Server%20In%205%20Minutes%20-%20nixCraft.pdf).
The original repo can be [found here](https://github.com/Nyr/openvpn-install).

# How to get a server for free?

You can get server for free at [Oracle Cloud](https://cloud.oracle.com) using the "Always free" dedicated to testing the services. It gives access to small machine that are enough for setting up a server.
More information on this video (in french): https://www.youtube.com/watch?v=23NboTdWMXs

## Configure the NAT policy (network)

The network rules has to be managed to make the VPN server accessible.
Go to the subnet details page and click on the security list.

![image](https://github.com/kisina/vpn/assets/84073449/9bd6f351-948d-40d9-8703-4c9ec8d56046)

![image](https://github.com/kisina/vpn/assets/84073449/ba75764e-62bc-4b64-a896-c8430ec1ba99)

Add an Ingress Rule for TCP ports 943 and 443.

![image](https://github.com/kisina/vpn/assets/84073449/6f111d9b-271d-4f32-a3de-38cec1a3010a)

Add another Ingress Rule, this one for UDP port 1194 (used for the VPN tunnel):

![image](https://github.com/kisina/vpn/assets/84073449/17fabd8f-d4e2-4987-b19e-427f9a410875)

Note: this information is partially coming from that [blog](https://blogs.oracle.com/developers/post/launching-your-own-free-private-vpn-in-the-oracle-cloud).

# Install the VPN server

Update your system and laucnh the bash script from the linked mentioned in the introduction (check the latest version on the original repo).

# Install the VPN client

This depends on the OS, but for linux you could use an instruction like

```bash
sudo apt install openvpn
```

# Launch the client

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

# Test your connection and your new IP

https://whatismyipaddress.com/

# How relaunch the client?

Just execute
```bash
sudo openvpn --client --config /etc/openvpn/client.conf
```
