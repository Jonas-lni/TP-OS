Tu veux démarrer sur une **clé USB avec Ubuntu** pour **accéder aux fichiers système de ton disque (comme `/etc/shadow`)** afin de réinitialiser un mot de passe oublié ? C’est faisable en suivant ces étapes 👇

---

## 🧰 Matériel requis
- Une **clé USB bootable** avec Ubuntu (Live)
- L’ordinateur sur lequel tu veux réinitialiser le mot de passe

---

## 🔧 Étapes détaillées

### 1. ✅ Créer une clé USB bootable avec Ubuntu (si ce n’est pas encore fait)
Sur un autre PC, utilise un outil comme :
- **Rufus** (Windows)
- **balenaEtcher** (Linux/macOS/Windows)
- **Startup Disk Creator** (si tu es déjà sur Ubuntu)

Télécharge l’ISO ici : [https://ubuntu.com/download](https://ubuntu.com/download)

---

### 2. 🚀 Démarrer depuis la clé USB
- Insère la clé USB dans l’ordi bloqué
- Allume-le et appuie sur la touche de **boot menu** (`F12`, `ESC`, `F10`, etc. selon ton modèle)
- Choisis la clé USB comme périphérique de démarrage
- Dans le menu Ubuntu, choisis : **Try Ubuntu** (Essayer Ubuntu sans installer)

---

### 3. 🧭 Monter le disque dur
Dans Ubuntu Live :
1. Ouvre un terminal
2. Liste les disques :

```bash
lsblk
```

Tu verras un disque genre `/dev/sda1`, `/dev/nvme0n1p1`, etc. (cherche la partition où se trouve le système installé)

3. Monte la partition :

```bash
sudo mkdir /mnt/systeme
sudo mount /dev/sda1 /mnt/systeme
```

*(Remplace `/dev/sda1` par la bonne partition !)*

4. Accède au fichier shadow :

```bash
sudo nano /mnt/systeme/etc/shadow
```

---

### 4. 🧹 Effacer le mot de passe root ou d’un utilisateur

Dans `/etc/shadow`, tu verras des lignes comme :

```
nom_utilisateur:$6$.....:...
```

Supprime **le hash** (tout entre le 1er et 2e `:`) pour vider le mot de passe, par exemple :

```
nom_utilisateur::...
```

Ensuite, enregistre et quitte (`Ctrl + O`, `Entrée`, puis `Ctrl + X`).

---

### 5. 🧱 Réinstaller le disque si tu l’as démonté

```bash
sudo umount /mnt/systeme
```

---

### 6. 🔁 Redémarrer

Redémarre sans la clé USB. Tu devrais pouvoir te connecter **sans mot de passe** à la session utilisateur en question.

---

## 🚨 Attention sécurité :
- Cette méthode donne un accès total au système — donc protège ton BIOS/UEFI avec un mot de passe !
- Une fois reconnecté, pense à **remettre un mot de passe** :

```bash
passwd nom_utilisateur
```

---

Tu veux que je t’aide à trouver la bonne partition (`lsblk`, `mount`, etc.) si tu bloques là-dessus ?
