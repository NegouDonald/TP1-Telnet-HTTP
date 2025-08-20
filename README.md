# TP1 - Utilisation de Telnet pour requêtes HTTP

## 🎯 Objectif
Le but de ce TP est de comprendre le protocole HTTP en construisant manuellement des requêtes via **Telnet** vers un serveur Apache installé sur Ubuntu.  
Nous testons différentes requêtes (GET et POST) pour interagir avec le serveur et observer les réponses.

---

## ⚙️ Environnement utilisé
- Système : Ubuntu 22.04
- Serveur Web : Apache2
- Outil réseau : Telnet
- Fichiers créés/testés :
  - `donald.html` → page HTML
  - `logo.png` → image PNG (19,8 ko)
  - `test.php` (optionnel) → script pour réceptionner une requête POST

---

## 📝 Étapes réalisées

### 1. Vérifier que le serveur Apache fonctionne
```bash
sudo systemctl start apache2
curl http://localhost

