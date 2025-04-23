## Notions
Hyperviseur qui crée un environnement matériel virtualisé 
proxmox : outil de virtualisation au format ISO
VM : Linux et windows possible - mise en place d'un switch virtuel basic qui connecte les machine. 
Conainerisation: linux et windows pas possible (doker) -> WSL: c'est une 
![containirisation.png](../_resources)
Interfaces réseaux virtuelles - 
Emulation 
Emuler sur une machine, une console de jeu c'est possible
Para-Virtualisation : un driver qui accéde aux ressources sans les avoir virtuellement. 

## Type de virtualisation
**Virtualisation** Type1 (bare metal) on utilise dans l'industrie (VMware - hyperV). 
**Virtualisation** type2 (hosted ) on utilise dans les pc perso, utilisation personnelle.
![virtualisation.png](../_resources)

Lorsque les calculs sont nombreux : il vaut mieux ne pas virtualiser car on a besoin de beaucoup de ressources 

## Avantage de la virtualisation:
Moins de Consommation de l'énérgie 
Maintenance 
acquisition 
optimisation des ressources 
possibilité de maintien de vieux systèmes incompatibles avec les nouvelles générations de matériel 
Déplacement des serveurs d'un continent à un autre grâce à la virtualisation pour réduire les coûts 
La virtualisation touche tous les domaines de l'informatique 

## Inconvénients:
recours à des machines puissantes
mise en oeuvre plus délicate, administration
Attention au SPOF (single point of failure)
Performances réduites si le CPU doit être émulé
Parfois inadapté -> exemple : s'il y a beaucoup d'entrées et de sorties Inpu/output 

## TP:
Nous allons utilisé KVM pou r la virtualisation : C'est une virtualisation de type1 
on va utilisé QEMU pour émuler plusieurs processeurs 
on va rajouter Libvirt : librairie virtuelles 
integration avec des outils graphiques
Snapshot : il permet de réaliser une **photo ** 
live migration : migration à chaud - migration : déplacement d'une VM sans l'arrêter

## creation d'une vm via la commande virt-install: 
`sudo virt-install  --name=jonas --ram=2048 --vcpus=2 --disk path=/home/user18/TP-OS/VM/vm_zorin.qcow2 --cdrom=/home/user18/ISO/Zorin-OS-16.2-Lite-64-bit-r1.iso --os-variant=generic --network=default --graphics=spice`

## La réponse est : erreur

`sudo virt-install  --name=jonas --ram=2048 --vcpus=2 --disk path=/home/user18/TP-OS/VM/vm_zorin.qcow2 --cdrom=/home/user18/ISO/Zorin-OS-16.2-Lite-64-bit-r1.iso --os-variant=generic --network=default --graphics=spice
WARNING  il se peut que /home/user18/ISO/Zorin-OS-16.2-Lite-64-bit-r1.iso ne soit pas accessible à l’hyperviseur. Vous devrez fournir à l’utilisateur « libvirt-qemu » des permissions de recherche pour les répertoires suivants : ['/home/user18']
WARNING  il se peut que /home/user18/TP-OS/VM/vm_zorin.qcow2 ne soit pas accessible à l’hyperviseur. Vous devrez fournir à l’utilisateur « libvirt-qemu » des permissions de recherche pour les répertoires suivants : ['/home/user18']
WARNING  il se peut que /home/user18/ISO/Zorin-OS-16.2-Lite-64-bit-r1.iso ne soit pas accessible à l’hyperviseur. Vous devrez fournir à l’utilisateur « libvirt-qemu » des permissions de recherche pour les répertoires suivants : ['/home/user18']
WARNING  Using --osinfo generic, VM performance may suffer. Specify an accurate OS for optimal results.
Début d’installation…
ERROR    Cannot access storage file '/home/user18/TP-OS/VM/vm_zorin.qcow2' (as uid:64055, gid:109): Permission denied
L’installation du domaine ne semble pas avoir réussi.
Si elle a réussi, vous pouvez démarrer le domaine en lançant :
 virsh --connect qemu:///system start jonas
sinon, recommencer l’installation.`

# solution 
## Donner les droits d'accés au dossier et fichiers : 
L'erreur que tu rencontres vient d’un **problème de permissions** : l’utilisateur `libvirt-qemu`, utilisé par le service `libvirt`, **n’a pas accès** aux fichiers de ton dossier personnel (`/home/user18`).

---

## 🔐 Explication rapide

`virt-install` s’exécute via `libvirt`, qui utilise le compte système `libvirt-qemu`. Ce compte ne peut pas lire ton dossier personnel par défaut (à cause des permissions de sécurité Linux).

---

## ✅ Solution : Donner les droits d’accès au répertoire

### Option 1 : Modifier les permissions avec `chmod +x`

Donne les droits de traversée (recherche) au groupe "others" sur ton dossier personnel **et les sous-dossiers concernés** :

```bash
chmod +x /home/user18
chmod +x /home/user18/TP-OS
chmod +x /home/user18/TP-OS/VM
chmod +x /home/user18/ISO
```

💡 Cela ne rend pas les fichiers lisibles, mais permet au processus `libvirt-qemu` de traverser les répertoires.

# Réessayer:
`sudo virt-install  --name=jonas --ram=2048 --vcpus=2 --disk path=/home/user18/TP-OS/VM/vm_zorin.qcow2 --cdrom=/home/user18/ISO/Zorin-OS-16.2-Lite-64-bit-r1.iso --os-variant=generic --network=default --graphics=spice`

**Installation réussie**

Dans le cas de Monsieur Girault: 
les 50 VM qu'il gére, il les 
Chaque VM est déstinée à un service : chaque VM est un serveur 

On peut automatiser le mount 

Un user ne doit pas etre mis sur un serveur, si on lui donne accés, il doit avoir des droits restreints


Pour **afficher ta VM démarrée** (c’est-à-dire voir son écran comme si tu étais devant un vrai PC), tu as plusieurs options selon le type de console graphique que tu utilises (Spice, VNC, etc.).

---

## 🧭 1. Vérifier si la VM est bien en cours d'exécution

```bash
sudo virsh list
```

Tu verras quelque chose comme :

```
 Id    Name                           State
----------------------------------------------------
 2     jonas                          running
```

---

## 🖥️ 2. Ouvrir l'affichage graphique (console de la VM)

### 💡 Si tu es en SPICE (comme dans ta commande `virt-install`)

Utilise :

```bash
virt-viewer jonas
```

Si ce n’est pas installé :

```bash
sudo apt install virt-viewer
```

Ou, avec interface plus complète :

```bash
virt-manager
```

Tu peux aussi lancer :

```bash
sudo virt-manager
```

Puis double-cliquer sur la VM « jonas » pour ouvrir la console.

---

## 🖧 3. Alternative : connexion VNC (si configuré)

Si la VM utilise VNC au lieu de SPICE :

```bash
sudo virsh vncdisplay jonas
```

Tu obtiendras un port comme `:0`, que tu peux ouvrir avec un client VNC :

```bash
vncviewer localhost:5900
```

(`:0` → port 5900, `:1` → port 5901, etc.)

---

## 📍 En résumé :

| Action                            | Commande                                  |
|-----------------------------------|--------------------------------------------|
| Voir si la VM est en marche       | `sudo virsh list`                          |
| Voir la console graphique (SPICE) | `virt-viewer jonas` ou `virt-manager`      |
| Afficher via VNC                  | `sudo virsh vncdisplay jonas`              |

---

Tu veux que je t’aide à configurer ta VM pour démarrer automatiquement avec une interface VNC ou SPICE à chaque boot ?


## 5.6 Ajouter un canal de type channel/qemu-guest-agent

**la commande qemu-guest-agent et sudo virsh guestinfo --domain jonas (le nom de la machine dans ce cas est jonas)** dans le **virt-manager** : on ajoute un matériel **canal** on ajoute l'agent et puis dans l'hyperviseur on tape la commande suivante **sudo virsh guestinfo --domain jonas** et on a toutes les informations suivante :

`sudo virsh guestinfo --domain jonas`
user.count          : 1
user.0.name         : jonas
user.0.login-time   : 1745413470796
os.id               : zorin
os.name             : Zorin OS
os.pretty-name      : Zorin OS 16.2
os.version          : 16.2
os.version-id       : 16
os.machine          : x86_64
os.kernel-release   : 5.15.0-138-generic
os.kernel-version   : #148~20.04.1-Ubuntu SMP Fri Mar 28 14:32:35 UTC 2025
timezone.name       : CEST
timezone.offset     : 7200
hostname            : jonas-Standard-PC-i440FX-PIIX-1996
fs.count            : 3
fs.0.name           : sda5
fs.0.mountpoint     : /
fs.0.fstype         : ext4
fs.0.total-bytes    : 9405779968
fs.0.used-bytes     : 9204039680
fs.0.disk.count     : 1
fs.0.disk.0.alias   : hda
fs.0.disk.0.serial  : QEMU_HARDDISK_QM00001
fs.0.disk.0.device  : /dev/sda5
fs.1.name           : sda1
fs.1.mountpoint     : /boot/efi
fs.1.fstype         : vfat
fs.1.total-bytes    : 535805952
fs.1.used-bytes     : 4096
fs.1.disk.count     : 1
fs.1.disk.0.alias   : hda
fs.1.disk.0.serial  : QEMU_HARDDISK_QM00001
fs.1.disk.0.device  : /dev/sda1
fs.2.name           : sdc1
fs.2.mountpoint     : /media/jonas/fc44f084-4719-4736-b047-48d1a119fddc
fs.2.fstype         : ext4
fs.2.total-bytes    : 4919664640
fs.2.used-bytes     : 24576
fs.2.disk.count     : 1
fs.2.disk.0.alias   : hdd
fs.2.disk.0.serial  : QEMU_HARDDISK_QM00004
fs.2.disk.0.device  : /dev/sdc1
if.count            : 2
if.0.name           : lo
if.0.hwaddr         : 00:00:00:00:00:00
if.0.addr.count     : 2
if.0.addr.0.type    : ipv4
if.0.addr.0.addr    : 127.0.0.1
if.0.addr.0.prefix  : 8
if.0.addr.1.type    : ipv6
if.0.addr.1.addr    : ::1
if.0.addr.1.prefix  : 128
if.1.name           : ens3
if.1.hwaddr         : 52:54:00:11:5a:bb
if.1.addr.count     : 2
if.1.addr.0.type    : ipv4
if.1.addr.0.addr    : 192.168.122.87
if.1.addr.0.prefix  : 24
if.1.addr.1.type    : ipv6
if.1.addr.1.addr    : fe80::f578:bae5:eed3:18a9
if.1.addr.1.prefix  : 64
***
