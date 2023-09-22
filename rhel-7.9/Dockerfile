FROM centos:7

RUN yum install -y qemu-img libguestfs-tools-c
ADD rhel-server-7.9-update-12-x86_64-kvm.qcow2 /disk/

# Modify the qcow2 image to set ifnames=1
RUN guestmount -a /disk/rhel-server-7.9-update-12-x86_64-kvm.qcow2 -i /mnt && \
    sed -i 's/net.ifnames=0/net.ifnames=1/g' /mnt/boot/grub2/grub.cfg && \
    guestunmount /mnt
