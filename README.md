# ⛏️ Kryptex AutoSwitch Linux

AutoSwitch communautaire et non officiel permettant d'utiliser **Kryptex sous Ubuntu/Linux**.

## 🚀 Fonctionnalités

- Benchmark automatique du CPU et du GPU
- AutoSwitch CPU et GPU indépendants
- Compare automatiquement la rentabilité des monnaies compatibles
- Bascule automatiquement vers la monnaie la plus rentable
- Actualisation de la rentabilité toutes les 60 secondes
- Changement uniquement si le gain est suffisamment intéressant
- Conservation des benchmarks entre les lancements
- Nouveau benchmark automatique après mise à jour d'un mineur
- Téléchargement et mise à jour automatique des mineurs
- Affichage des gains en **€ ou $**
- Affichage du **TOTAL BENCH**
- Affichage du **TOTAL ACTUEL basé sur le hashrate réel**
- Estimation des gains par jour, 30 jours et année
- **0 % de frais supplémentaires prélevés par AutoSwitch**

## 📦 Installation

Téléchargez `kryptex-autoswitch`, puis :

```bash
wget https://github.com/Dorian-360/Kryptex-autoswitch/releases/download/v1.3/kryptex-autoswitch.V1.3
chmod +x kryptex-autoswitch
sudo ./kryptex-autoswitch --cpu 32 --gpu 1
```

Au premier lancement, le script demande votre **Mining Username Kryptex**.

Vous pouvez le retrouver dans votre compte Kryptex. Il ressemble à :

```text
krxX3QD88J
```

Entrez uniquement la partie `krx...`.

Le nom de votre machine est automatiquement ajouté comme nom de worker.

## ⚙️ Commandes

### CPU + GPU

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1
```

### GPU uniquement

```bash
sudo ./kryptex-autoswitch --cpu 0 --gpu 1
```

### CPU uniquement

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 0
```

### Refaire tous les benchmarks

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1 --rebench
```

`--cpu 32` correspond au nombre de threads CPU à utiliser.

## 📊 Affichage

Le tableau affiche :

- la rentabilité de chaque monnaie ;
- la monnaie actuellement minée sur CPU et GPU ;
- le **TOTAL BENCH**, calculé à partir des benchmarks ;
- le **TOTAL ACTUEL**, recalculé à partir du hashrate réellement produit par les mineurs ;
- les gains estimés par jour, 30 jours et année.

## ❤️ Soutenir le projet

AutoSwitch ne prélève **aucun frais supplémentaire : 0 %**.

Si le projet vous est utile, vous pouvez soutenir son développement en créant votre compte Kryptex avec mon lien :

https://www.kryptex.com/?ref=95ac8ffd

Merci et bon minage ! ⛏️

> Projet communautaire non officiel, indépendant et non affilié à Kryptex.
