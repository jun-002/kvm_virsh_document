# kvm_virsh_document
# This is the document to use virsh cheating sheet

# get list vm 
```sh
$ sudo virsh list
```
# get dhcp IPs
```sh
$ sudo virsh net-dhcp-leases default
```
# get network interface and IP
```sh
$ sudo virsh domifaddr testvm
```
# get IP from VM mac address
```sh
$ sudo virsh dumpxml testvm | grep "mac address"
$ sudo virsh dumpxml testvm | grep "mac address" | awk -F\' '{ print $2 }'
```
# vm clone
```sh
$ sudo virt-clone --orignal testvm --name testvm-clone --auto-clone
$ xauth add $(xauth -f ~/.Xauthority list | tail -1)
```
