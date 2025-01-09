# Tp volumes logiques

## Disques virtuels
 
## Notion:
wubuntu : interface de microsoft sous ubuntu **intéressant**

  **dd if=/dev/zero of=vdiskX count=X bs=1G status=progress** X c'est le numéro du vdisk
  
  **losetup -Pf --show vdisk3**

 Vétrification **ls -lh**

**pvremove  --force  --force /dev/loop34** ->  effacer les loop lié à un disque virtuel

## 2/Création d'un PV:
root@EECS18:/home/user18/vdisks# **pvcreate /dev/loop33** création d'un PV associé au disk1

root@EECS18:/home/user18/vdisks# **pvcreate /dev/loop34** création d'un PV associé au disk2

root@EECS18:/home/user18/vdisks# **pvcreate /dev/loop35** création d'un PV associé au disk3

root@EECS18:/home/user18/vdisks# **pvcreate /dev/loop36** création d'un PV associé au disk4

## 3/Creation d'un VG:

**vgcreate mousquetaire /dev/loop33** ->  creation du VG demandé dans la ligne 3.1 du TP du 9 janvier 2025

**vgextend mousquetaire /dev/loop34** -> extension du VG mousquetaire en ajoutant le disque de 2GO (vdisk2) on obtient un espace de 3GO

## 4/ Construction initiale LV:

**lvcreate -L 700MB -n atos mousquetaire** -> création du volume atos

**lvcreate -L 1400MB -n aramis mousquetaire** -> création du volume aramis


