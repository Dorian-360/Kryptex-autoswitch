# ⛏️ Kryptex AutoSwitch Linux

AutoSwitch communautaire et non officiel permettant d'utiliser **Kryptex sous Ubuntu/Linux**.

Le script gère automatiquement le minage **CPU et GPU**, compare la rentabilité des différentes monnaies compatibles et sélectionne la plus rentable.

## 🚀 Fonctionnalités

- 🖥️ Benchmark automatique du CPU et du GPU
- 🔄 AutoSwitch CPU et GPU indépendants
- 💰 Comparaison automatique de la rentabilité des monnaies compatibles
- ⛏️ Bascule automatique vers la monnaie la plus rentable
- ⏱️ Actualisation de la rentabilité toutes les 60 secondes
- 📈 Changement uniquement si le gain est suffisamment intéressant
- 💾 Conservation des benchmarks entre les lancements
- 🔄 Nouveau benchmark automatique après mise à jour d'un mineur
- 📥 Téléchargement et mise à jour automatique des mineurs
- 🔎 Vérification périodique des mises à jour des mineurs
- 💶 Affichage des gains en **€ ou $**
- 📊 Affichage du **TOTAL BENCH**
- ⚡ Affichage du **TOTAL ACTUEL basé sur le hashrate réel**
- 📅 Estimation des gains par jour, 30 jours et année
- ❤️ **0 % de frais supplémentaires prélevés par AutoSwitch**

---

## 👤 1. Créer un compte Kryptex

Vous devez disposer d'un compte Kryptex pour utiliser AutoSwitch.

### ❤️ Soutenir le projet

AutoSwitch ne prélève **aucun frais supplémentaire : 0 %**.

Si le projet vous est utile, vous pouvez soutenir son développement en créant votre compte Kryptex avec mon lien de parrainage :

https://www.kryptex.com/?ref=95ac8ffd

Cela permet de soutenir le développement du projet sans ajouter de frais au script.

---

## 📦 2. Installation

Téléchargez la dernière version :

```bash
cd ~
wget https://github.com/Dorian-360/Kryptex-autoswitch/releases/download/v1.3/kryptex-autoswitch.V1.3
mv kryptex-autoswitch.V1.3 kryptex-autoswitch
chmod +x kryptex-autoswitch
```

Puis lancez AutoSwitch :

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1
```

> `--cpu 32` correspond au nombre de threads CPU à utiliser. Adaptez cette valeur à votre processeur.

---

## 🔑 3. Identifiant Kryptex

Au premier lancement, le script vous demande votre **Mining Username Kryptex**.

Il ressemble à ceci :

```text
krxX3QD88J
```

Entrez uniquement la partie :

```text
krx...
```

Le nom de votre machine est automatiquement ajouté comme nom de worker.

Exemple :

```text
krxX3QD88J.9950x-01
```

La configuration est ensuite enregistrée pour les prochains lancements.

---

## ⚙️ Commandes

### 🖥️ CPU + GPU

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1
```

### 🎮 GPU uniquement

```bash
sudo ./kryptex-autoswitch --cpu 0 --gpu 1
```

### 🧠 CPU uniquement

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 0
```

### 🔄 Refaire tous les benchmarks

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1 --rebench
```

---

## 📊 Affichage

AutoSwitch affiche en temps réel :

- la rentabilité de chaque monnaie compatible ;
- la monnaie actuellement sélectionnée pour le CPU ;
- la monnaie actuellement sélectionnée pour le GPU ;
- le hashrate actuel des mineurs ;
- les gains estimés en **€ ou $** ;
- les estimations par jour, 30 jours et année.

### TOTAL BENCH

Le **TOTAL BENCH** correspond aux gains estimés à partir des hashrates enregistrés pendant les benchmarks.

### TOTAL ACTUEL

Le **TOTAL ACTUEL** utilise le hashrate réellement produit par les mineurs en cours d'exécution afin d'obtenir une estimation plus proche des performances actuelles de la machine.

---

## 🔄 Mises à jour

AutoSwitch peut vérifier les nouvelles versions des mineurs utilisés.

Lorsqu'une nouvelle version d'un mineur est installée, les benchmarks concernés peuvent être refaits afin de prendre en compte les performances de la nouvelle version.

Les benchmarks déjà valides sont conservés afin d'éviter de refaire inutilement tous les tests.

---

## ❤️ Soutenir Kryptex AutoSwitch Linux

Le script AutoSwitch prélève :

**0 % de frais supplémentaires.**

Si vous souhaitez soutenir le développement du projet, vous pouvez simplement créer votre compte Kryptex avec mon lien :

https://www.kryptex.com/?ref=95ac8ffd

Merci et bon minage ! ⛏️

---

> ⚠️ **Avertissement**
>
> Kryptex AutoSwitch Linux est un projet communautaire non officiel, indépendant et non affilié à Kryptex.
>
> Les estimations de rentabilité peuvent évoluer rapidement selon le cours des monnaies, la difficulté du réseau, les performances du matériel et les données fournies par les pools/services utilisés.
