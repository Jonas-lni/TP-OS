Faire un montage **NFS (Network File System)** sur Ubuntu permet de **partager des dossiers entre plusieurs machines** sur un réseau local. Voici un guide complet, simple et clair pour **monter un dossier NFS sur un client Ubuntu**.

---

## 📦 Étape 1 : Installer les paquets nécessaires

### Sur le **client NFS** (celui qui veut accéder au dossier partagé) :

```bash
sudo apt update
sudo apt install nfs-common
```

---

## 🖥️ Étape 2 : Vérifier que le serveur NFS est prêt

Sur le **serveur NFS** (celui qui partage le dossier), tu dois avoir :

1. Un dossier partagé via `/etc/exports`
2. Le service `nfs-kernel-server` en fonctionnement

Exemple de ligne dans `/etc/exports` :

```
/srv/partage 192.168.1.0/24(rw,sync,no_subtree_check)
```

Et sur le serveur :

```bash
sudo exportfs -a
sudo systemctl restart nfs-kernel-server
```

---

## 📡 Étape 3 : Trouver les partages disponibles

Sur le **client**, pour voir ce que propose le serveur :

```bash
showmount -e IP_DU_SERVEUR
```

Exemple :

```bash
showmount -e 192.168.1.10
```

Tu verras quelque chose comme :

```
Export list for 192.168.1.10:
/srv/partage 192.168.1.0/24
```

---

## 📁 Étape 4 : Monter le dossier NFS manuellement

Crée un point de montage :

```bash
sudo mkdir -p /mnt/nfs_partage
```

Puis monte :

```bash
sudo mount 192.168.1.10:/srv/partage /mnt/nfs_partage
```

*(remplace bien l’IP et le chemin du partage selon ta config)*

Tu peux maintenant accéder aux fichiers partagés :

```bash
ls /mnt/nfs_partage
```

---

## 🔁 Étape 5 : Monter automatiquement au démarrage

Ajoute cette ligne dans `/etc/fstab` :

```bash
192.168.1.10:/srv/partage /mnt/nfs_partage nfs defaults 0 0
```

Teste le montage sans redémarrer :

```bash
sudo mount -a
```

---

## ⚠️ Astuces et Dépannage

- Si tu as des erreurs de permission, vérifie les droits sur le dossier partagé et la configuration de `/etc/exports`.
- Les firewalls (UFW, etc.) peuvent bloquer le NFS : ouvre les ports si nécessaire (2049 pour NFS v4).
- Utilise `nfs4` dans `/etc/fstab` si tu veux forcer NFS version 4.

Dans le cas de l'école :

`mount -t nfs 192.168.150.14:/var/lib/libvirt/iso /nchemin/vers/le/dossier`

dans le dossier créé, il faut copier et coller les fichiers dans le dossier que tu veux utiliser pour l'emplacement des fichiers 

---

Installation du package nsf-serveur 
etc/exports 
/var/lib/libvirt/iso *(ro,sync,no_subtree_check)