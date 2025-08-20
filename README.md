 
````markdown
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
````

### 2. Ouvrir une session Telnet sur le port HTTP (80)

```bash
telnet localhost 80
```

---

## 📌 Requêtes HTTP testées

### 🔹 GET d’une page HTML (`donald.html`)

```
GET /donald.html HTTP/1.1
Host: localhost

```

### 🔹 GET d’une image PNG (`logo.png`)

```
GET /logo.png HTTP/1.1
Host: localhost

```

👉 La réponse contient le flux binaire de l’image, affiché sous forme de caractères illisibles dans Telnet (normal).

### 🔹 POST de données simples (`test.php`)

Fichier PHP minimal dans `/var/www/html/test.php` :

```php
<?php
echo "Vous avez envoyé : ";
print_r($_POST);
?>
```

Requête POST envoyée :

```
POST /test.php HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded
Content-Length: 11

nom=Donald
```

Réponse du serveur :

```
Vous avez envoyé : Array ( [nom] => Donald )
```

---

## ⚠️ Limites rencontrées

* Telnet est adapté aux **requêtes textuelles** (GET/POST avec données simples).
* Il n’est **pas adapté à l’envoi de fichiers binaires** (comme une image PNG) via POST.
  Pour tester correctement l’upload de fichiers, il faudrait utiliser un outil comme `curl` ou `netcat`.

---

## ✅ Conclusion

Ce TP montre que :

* HTTP repose sur des requêtes textuelles que l’on peut construire manuellement.
* Telnet permet de visualiser directement les échanges client ↔ serveur.
* On peut tester les méthodes GET et POST, mais l’envoi de fichiers binaires n’est pas pratique via Telnet.

```

Tu peux maintenant **copier-coller tel quel** dans ton dépôt GitHub.  

Si tu veux, je peux aussi te fournir **les commandes Git exactes** pour créer le dépôt et publier ce TP avec tes fichiers. Veux‑tu que je fasse ça ?
```

