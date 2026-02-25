# Installation d’un serveur Minecraft 1.15.1 (Spigot/Bukkit) sur Ubuntu

Ce guide explique étape par étape comment installer un **serveur Minecraft 1.15.1 Spigot/Bukkit** sur une machine virtuelle Ubuntu, par exemple sous **Proxmox VE**.

---

## Pré-requis

- Une VM Ubuntu (avec accès SSH ou console)
- Java installé (OpenJDK 11 recommandé)
- Un lien de téléchargement direct vers le serveur `.jar`
- Accès aux ports réseau (ouverture du port 25565)

---

## 1. Mise à jour de l’environnement

Connectez-vous à votre VM Ubuntu puis :

```bash
sudo apt update
sudo apt upgrade -y
```
---

## 2. Installer Java
```bash
sudo apt install openjdk-11-jre -y
java -version
```

---

## 3. Préparer le dossier du serveur

```bash
mkdir ~/minecraft
cd ~/minecraft
```

---

## 4. Télécharger le serveur

```bash
wget https://download.spigotmc.org/resources/loup-garou-squeezie.76251/files/LoupGarou.jar
ls
```

---

## 5. Premier lancement (pour générer les fichiers)

```bash
java -Xms1G -Xmx2G -jar nomdufichier.jar nogui
```

---

## 6. Accepter la licence

```bash
nano eula.txt
eula=false
```

Puis :
CTRL + X
Y
Entrée

---

## 7. Relancer le serveur

```bash
java -Xms1G -Xmx2G -jar nomdufichier.jar nogui
```

Code : Done! For help, type "help"

## 8. Ajouter les plugins

Si tu dois ajouter : 
° LoupGarou
° ProtocolLib

Déposez les plugins .jar dans :

```bash
~/minecraft/plugins
```

Puis redémarrez le serveur pour appliquer les plugins.

--- 

## 9. Ouvrir le port (important)

```bash
sudo ufw allow 25565
```

---

## 10. Connexion au serveur

Code : IP_DU_SERVEUR:25565

---

## 11. Conseils & bonnes pratiques

Exécuter le serveur en arrière-plan

Installez screen :

```bash
sudo apt install screen -y
screen -S minecraft
```

Lancez le serveur dedans (CTRL+A, D pour détacher).

Récupérez la session :

```bash
screen -r minecraft
```
