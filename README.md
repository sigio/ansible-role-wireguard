
# Ansible-role-wireguard

To use this role, you need to define a dictionary of wireguard_peers, for example in your group_vars/all
or somewhere equivalent.
```yaml
  # Inventory hostname / machine name IP-in-VPN Public/Peer IP  Pubkey
  wireguard_peers:
    - { name: "some-wireguard-host", ip: "10.20.30.1",   endpoint: "1.2.3.4", pubkey: "wg-pubkey-base64" }
    - { name: "another-wg-host",     ip: "10.20.30.2",   endpoint: "1.3.5.7", pubkey: "wg-pubkey-base64" }
    - { name: "ya-wg-host",          ip: "10.20.30.3",   endpoint: "2.4.6.8", pubkey: "wg-pubkey-base64" }
  ...
```
# Usage

You will normally need to run this role at least 2 times on a new host. The first run will install wireguard
software, build the dkms module (if needed) and generate a private and public-key.

The public-key needs to be added to the wireguard_peers listing. as seen above.

On a subsequent run of this play/role, all hosts will create connections with eachother, using the pub-key
and peer-ip information from the wireguard_peers table.


