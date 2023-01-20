# kvm_virsh_document
# This is the document to use virsh cheating sheet

# get list vm 
$ sudo virsh list
# get dhcp IPs
$ sudo virsh net-dhcp-leases default
# get network interface and IP
$ sudo virsh domifaddr testvm
# get IP from VM mac address
$ sudo virsh dumpxml testvm | grep "mac address"
$ sudo virsh dumpxml testvm | grep "mac address" | awk -F\' '{ print $2 }'
# vm clone
$ sudo virt-clone --orignal testvm --name testvm-clone --auto-clone
$ xauth add $(xauth -f ~/.Xauthority list | tail -1)
 

