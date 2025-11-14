# How-to-Increase-promox-partition

> https://www.youtube.com/watch?v=CcD-9JrRw0k&t=95s
> https://syncbricks.com/how-to-increase-ubuntu-vg-volume-size-lvm/
> https://syncbricks.com/how-to-increase-xfs-root-partition/

Before you begin you must use the below command to check the partition details in your Linux server
```
lsblk
```

```
df -h
```
First you will need to grow the partition. For example, your disk is sda and your partition is 3. so use the following command
```
sudo growpart /dev/sda 3
```
Si ya une erreur

Supprimer les journeaux

```
sudo journalctl --vacuum-time=3d
sudo rm -rf /var/log/*.gz
sudo rm -rf /var/log/*.1
```
On essaie d'agrandir 
```
sudo growpart /dev/sda 3
```
Verification
```
lsblk
```
Options to Extend the Volume Size
I am giving you 2 options

Option1 : Use 100% Avaialble Size
If you want to use 100% available of sd3 then use below command
```
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
```
Option2 : Add a specified size
If you want to add specified size use below command for example I want to add addtional 5GB then i will use below

```
sudo lvextend -L+5G /dev/mapper/ubuntu--vg-ubuntu--lv
```
Final Step
Now depending upon your file system you can use below comamnd

for ext4
```
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```
for xfs
```
sudo xfs_growfs /dev/mapper/ubuntu--vg-ubuntu--lv
```



```
lsblk
```

```
lsblk
```

```
lsblk
```

```
lsblk
```

```
lsblk
```

```
lsblk
```
