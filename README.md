Ansible Openswan Role
===

# Variables
```
## Public IP A) set manuly or B) Use rule
openswan_public_address_rule  :
                                - regx      : "192.168.1.[1-254]"
                                  match     : True
#openswan_public_address       : "{{ansible_all_ipv4_addresses[1]}}"

## Private IP A) set manuly or B) Use rule
#openswan_private_address     : "{{ansible_all_ipv4_addresses[0]}}"
openswan_private_address_rule :
                                - regx      : "10.0.2.*"
                                  match     : True


openswan_vpn_range            : "172.16.1.10-172.16.1.254" # IP's to give to the connecting clients
openswan_vpn_gateway          : "172.16.1.8"               # Server IP

# Address ranges that may live behind a NAT router
openswan_virtual_private      :
                                - name    : VPN IP Range
                                  v       : 4
                                  network : "172.16.0.0/12"

                                - name    : Private Network
                                  v       : 4
                                  network : "{{ openswan_private_address }}/24"

openswan_auth_method          : "psk"   # "psk" or "rsa"

# Option "psk"
openswan_shared_secret        : "secret_shared_password"

## Option "rsa"
openswan_cert_password        : "123456"
openswan_left_fqdn            : "host.example.com"
openswan_left_cert_file       : "host.example.com.pem"

## Users
openswan_users                :
                                - name   : test
                                  secret : test_password

## Openswan General options
openswan_nat_traversal        : "yes" # "yes" or "no"
openswan_ppp_debug            : "True"
```
