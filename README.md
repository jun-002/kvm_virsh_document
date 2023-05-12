## kvm_virsh_document
### This virsh cheat sheet

### get list vm 
```sh
$ sudo virsh list
```
### start/stop/shutdown VM
```sh
$ sudo start testvm
$ sudo reset testvm
$ sudo destroy testvm_id
```
### get dhcp IPs
```sh
$ sudo virsh net-dhcp-leases default
```
### get network interface and IP
```sh
$ sudo virsh domifaddr testvm
```
### get IP from VM mac address
```sh
$ sudo virsh dumpxml testvm | grep "mac address"
$ sudo virsh dumpxml testvm | grep "mac address" | awk -F\' '{ print $2 }'
```
### vm clone
```sh
$ sudo virt-clone --orignal testvm --name testvm-clone --auto-clone
$ xauth add $(xauth -f ~/.Xauthority list | tail -1)
```
### vm get disks
```
$ sudo virsh domblklist lii279a1 --details
Type       Device     Target     Source
------------------------------------------------
block      disk       sda        /dev/mapper/lii279a1_rootvg-oslv
block      disk       sdd        /dev/lii279a1_iappjfs_1_l/lvol1
block      disk       sde        /dev/lii279a1_iappjfs_1_l/lvol2
block      disk       sdf        /dev/mapper/lii279a1_iappjfs_1_l-lvol3--27aa
block      disk       sdg        /dev/mapper/lii279a1_dappjfs_1_l-lvol1--086a
block      disk       sdh        /dev/mapper/3600507680c80038f7000000000002a57
block      disk       sdi        /dev/mapper/36005076801808770e8000000000008ea
block      disk       sdj        /dev/mapper/lii279a1_dappjfs_1_l-2226
block      disk       sdk        /dev/mapper/lii279a1_dappjfs_1_l-2227
block      disk       sdl        /dev/mapper/3600507680c8080cca000000000001479
block      disk       sdm        /dev/mapper/3600507680c8080cca00000000000147c
file       cdrom      hda        /tmp/rhel-server-7.9-x86_64-dvd.iso
```

### virsh get disk location of all VMs in a Array
```bash
declare -a my_array=($(for vm in $(virsh list --all --name); do
    virsh domblklist $vm | awk '/dev/{print $2}'
done))
```

