# ⛏️ Kryptex AutoSwitch Linux

AutoSwitch communautaire et non officiel permettant d'utiliser **Kryptex sous Ubuntu/Linux**.

Le script gère automatiquement le minage **CPU et GPU**, compare la rentabilité des différentes monnaies compatibles et sélectionne automatiquement la plus rentable.
<img width="684" height="402" alt="Capture d&#39;écran 2026-09-29 203738" src="https://github.com/user-attachments/assets/bb6561a7-9371-43f9-ae99-587cf63b7113" />

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
- 💱 Conversion automatique des gains par Kryptex
- 💶 Affichage des estimations en **€ ou $**
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

Cela permet de soutenir le développement du projet sans ajouter de frais supplémentaires au script.

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

Entrez uniquement votre identifiant `krx...`.

Le nom de votre machine est automatiquement ajouté comme nom de worker.

La configuration est ensuite enregistrée automatiquement pour les prochains lancements.

---

## 💱 4. Conversion automatique des gains

AutoSwitch peut miner différentes cryptomonnaies en fonction de leur rentabilité.

**Vous n'avez rien à convertir manuellement.**

En utilisant votre **Mining Username Kryptex**, les monnaies minées sont automatiquement converties par Kryptex et les gains sont crédités sur votre compte **en Bitcoin (BTC)**.

```text
AutoSwitch
     ↓
Recherche la monnaie la plus rentable
     ↓
CPU et GPU minent automatiquement
     ↓
Kryptex reçoit les gains
     ↓
Conversion automatique
     ↓
Solde crédité en Bitcoin (BTC)
```

Vous pouvez donc laisser AutoSwitch passer automatiquement d'une monnaie à une autre sans modifier votre configuration.

### 💳 Retrait des gains

Au moment du retrait, Kryptex propose différentes méthodes de paiement.

Selon les options disponibles sur Kryptex et dans votre région, les retraits peuvent notamment être proposés en différentes cryptomonnaies ou via d'autres méthodes de paiement.

Il n'est donc pas nécessaire de choisir à l'avance la monnaie que doit miner AutoSwitch :

**AutoSwitch recherche la meilleure rentabilité et Kryptex s'occupe de la conversion automatique des gains.**

---

## ⚙️ 5. Commandes

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

### Nombre de threads CPU

La valeur suivant `--cpu` correspond au nombre de threads CPU utilisés.

Par exemple :

```bash
--cpu 32
```

utilise **32 threads CPU**.

Vous pouvez réduire cette valeur si vous souhaitez conserver une partie de la puissance CPU disponible pour d'autres tâches.

---

## 📊 6. Affichage

AutoSwitch affiche en temps réel :

- la rentabilité de chaque monnaie compatible ;
- la monnaie actuellement sélectionnée pour le CPU ;
- la monnaie actuellement sélectionnée pour le GPU ;
- le hashrate actuel des mineurs ;
- les gains estimés en **€ ou $** ;
- les estimations par jour, 30 jours et année.

### 📊 TOTAL BENCH

Le **TOTAL BENCH** correspond aux gains estimés à partir des hashrates enregistrés pendant les benchmarks.

Exemple :

```text
┌─────────────────────────────── TOTAL BENCH ────────────────────────────────┐
│  CPU: XMR        0.8167 €/j   +   GPU: PRL        5.1782 €/j               │
│  TOTAL : 5.9949 €/jour   │   179.85 €/30j   │   2188.14 €/an               │
└────────────────────────────────────────────────────────────────────────────┘
```

### ⚡ TOTAL ACTUEL

Le **TOTAL ACTUEL** utilise le hashrate réellement produit par les mineurs en cours d'exécution.

Cela permet d'obtenir une estimation basée sur les performances actuelles de la machine et pas uniquement sur le benchmark initial.

Exemple :

```text
┌─────────────────────────────── TOTAL ACTUEL ───────────────────────────────┐
│  CPU: XMR       22.20 kH/s  →   0.8100 €/j                                │
│  GPU: PRL      169.52 TH/s  →   4.9765 €/j                                │
│  TOTAL : 5.7865 €/jour   │   173.60 €/30j   │   2112.07 €/an               │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔄 7. Mises à jour des mineurs

AutoSwitch gère automatiquement les mineurs nécessaires au fonctionnement des différents algorithmes.

Le script peut :

- détecter les versions installées ;
- rechercher de nouvelles versions ;
- télécharger automatiquement les nouvelles versions ;
- conserver les benchmarks lorsque la version du mineur n'a pas changé ;
- invalider les benchmarks concernés lorsqu'un mineur est mis à jour ;
- refaire uniquement les benchmarks nécessaires.

Cela évite de refaire inutilement l'ensemble des benchmarks à chaque lancement.

Le contrôle des mises à jour est également effectué périodiquement pendant le fonctionnement d'AutoSwitch.

S'il n'y a aucune mise à jour, **le minage continue normalement sans interruption**.

---

## 🔄 8. Fonctionnement de l'AutoSwitch

La rentabilité est régulièrement recalculée.

```text
Benchmark CPU/GPU
       ↓
Calcul de la rentabilité
       ↓
Sélection des meilleures monnaies
       ↓
Minage CPU + GPU
       ↓
Actualisation de la rentabilité
       ↓
Une monnaie devient suffisamment plus rentable ?
       │
       ├── NON → le minage continue
       │
       └── OUI → AutoSwitch change de monnaie
```

Le CPU et le GPU sont gérés **indépendamment**.

Le CPU peut donc miner une monnaie pendant que le GPU en mine une autre.

---

## ❤️ Soutenir Kryptex AutoSwitch Linux

Kryptex AutoSwitch Linux prélève :

# **0 % de frais supplémentaires**

Aucun pourcentage supplémentaire n'est prélevé par AutoSwitch sur votre minage.

Si vous souhaitez soutenir le développement du projet, vous pouvez simplement créer votre compte Kryptex avec mon lien de parrainage :

https://www.kryptex.com/?ref=95ac8ffd

Cela permet de soutenir le développement du projet sans ajouter de frais supplémentaires au script.

**Merci et bon minage ! ⛏️**

---

## ⚠️ Avertissement

**Kryptex AutoSwitch Linux est un projet communautaire non officiel, indépendant et non affilié à Kryptex.**

Les estimations de rentabilité peuvent évoluer rapidement selon :

- le cours des cryptomonnaies ;
- la difficulté des réseaux ;
- les performances du matériel ;
- les frais propres aux logiciels de minage utilisés ;
- les données fournies par Kryptex et les pools ;
- les variations du hashrate réel.

Les valeurs affichées par AutoSwitch sont donc des **estimations** et ne garantissent pas les revenus réellement obtenus.
