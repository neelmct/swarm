## Unifi controller

### Volumes
`unifi/controller` and `unifi/mongo` **must** be created before deploy.
`unifi/mongo` **must** be 755 (`chmod 755`)

### Network
Unifi controller need to have direct access to the LAN, so i use a macvlan network

#### Setup macvlan network
**EACH** nodes
```
docker network create \
  --config-only \
  --subnet <LAN CIDR> \
  --gateway <GW @IP> \
  --opt parent=<IFACE> \
  --ip-range <subnet CIDR> \
  <service>_macvlan_config
```
Nota : \
--ip-range is a subnet of --subnet, all @ip will be taken from this range. \
--ip-range can be a /32, (one container, one ip) \
\
Manager **ONLY**
```
docker network create \
  --driver macvlan \
  --scope swarm \
  --config-from <service>_macvlan_config \
  <service>_macvlan
  ```
