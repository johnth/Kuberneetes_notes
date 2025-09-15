#make directories for disk mount(s)
mkdir /mnt/nvme1n1

# lsblk to list block devices
lsblk
# make filesystem ext4 on block device required from lsblk
sudo mkfs -t ext4 /dev/nvme1n1
# edit fstab with the id of disk from blkid command
blkid

# example:
`
/dev/nvme2n1: UUID="e3f52a38-4905-4464-bebe-a677dd97086a" BLOCK_SIZE="4096" TYPE="ext4"
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="62a898c2-2a55-4734-bba9-8806a024cd0b" BLOCK_SIZE="4096" TYPE="ext4"
/dev/nvme1n1p2: UUID="2de42746-e589-43f3-a16f-c23e529e34dc" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="a155b2b2-bc1b-4673-aa85-94f5ebd8e275"
/dev/nvme1n1p3: UUID="f0En9f-Zihn-8lFp-ZuwG-oHS5-yxiE-OVQFPa" TYPE="LVM2_member" PARTUUID="dca4ee40-3c07-4d8b-925f-1c6b0909c16a"
/dev/nvme1n1p1: UUID="BE3B-3F39" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="a2bdeb7c-fcdf-439c-abf9-707f4a9b7abe"
`
nano /etc/fstab

#add line(s) for mounting automatically at boot
UUID="e3f52a38-4905-4464-bebe-a677dd97086a" /mnt/nvme1n1 ext4 defaults 0 2

# restart/mount file system automatically second one prefferred
mount -a
systemctl daemon-reload