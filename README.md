# rc.hurricane

this is a rc style init script to setup a hurricane electric IPv6 tunnel. while created with slackware in mind, it should work on any linux based system.

## config

configuration is read from `rc.hurricane.conf`, most of the values are found on the
tunnel details page.

- `CLIENTIP` should be set to your external IPv6 address. the default value in the config uses myip.opendns.com to find this address.
- `SERVERIP` tunnel endpoint server IPv4 address
- `SERVERIPV6` tunnel endpoint server IPv6 address
- `CLIENTIPV6` tunnel endpoint client IPv6 address
- `NETWORK` routed IPv6 network address, without prefix
- `PREFIX` prefix length, 64 or 48
`NETWORK` and `PREFIX` are set from "Routed IPv6 Prefixes". For `2001:db8:dead:beef::/64` the values would look like `NETWORK=2001:db8:dead:beef::` and `PREFIX=64`
- `LOCALIPV6` address which should be set to a local device. has to be in the prefix defined in `NETWORK`. the default is `${NETWORK}1`
- `DEV` is set to the network device which should get the address defined as `LOCALIPV6`
- `TUNNELID` tunnel id from tunnel details
- `USERNAME` your hurricane electric username
- `PASSWORD` tunnel update key found in the advanced tab of tunnel details.

if these values are set, you can do the follwing things:

- `rc.hurricane update` update your external ipv4 address
- `rc.hurricane start` start the tunnel
- `rc.hurricane stop` stop the tunnel
- `rc.hurricane restart` stop and start the tunnel
- `rc.hurricane radvd` print a radvd.conf you can use if you want to advertise the route with radvd.