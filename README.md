# ⛏️ Kryptex AutoSwitch Linux V2.0

AutoSwitch communautaire et non officiel permettant d'utiliser **Kryptex sous Ubuntu/Linux**.

Le script gère automatiquement le minage **CPU et GPU**, compare la rentabilité des différentes monnaies compatibles et sélectionne automatiquement la plus rentable.

La V2.0 ajoute notamment la gestion automatique des profils GPU, le support multi-GPU, la recherche du meilleur rendement CPU et un suivi en temps réel du **hashrate et de la consommation électrique**.

<img width="684" height="402" alt="Kryptex AutoSwitch Linux" src="https://github.com/user-attachments/assets/bb6561a7-9371-43f9-ae99-587cf63b7113" />

---

## 🚀 Fonctionnalités

- 🖥️ Benchmark automatique du CPU et du GPU
- 🔄 AutoSwitch CPU et GPU indépendants
- 💰 Comparaison automatique de la rentabilité des monnaies compatibles
- ⛏️ Bascule automatique vers la monnaie la plus rentable
- ⏱️ Actualisation de la rentabilité toutes les 60 secondes
- 📈 Changement uniquement si le gain dépasse le seuil configuré
- 💾 Conservation des benchmarks entre les lancements
- 🔄 Nouveau benchmark uniquement lorsque cela est nécessaire
- 📥 Téléchargement et mise à jour automatique des mineurs
- 🔎 Vérification périodique des mises à jour des mineurs
- 🎮 Support de plusieurs GPU
- ⚡ Gestion automatique des profils GPU adaptés au matériel et à l'algorithme
- 💾 Cache local des profils GPU pour éviter les recherches inutiles
- 🛡️ Profils de secours lorsqu'aucun profil exact n'est disponible
- 🚫 Possibilité de désactiver la gestion automatique des profils GPU avec `--no-oc`
- 🧠 Mode `--cpu-efficient` pour rechercher automatiquement le nombre de threads offrant le meilleur rendement CPU
- 💾 Conservation du résultat du test d'efficience CPU entre les lancements
- 💱 Conversion automatique des gains par Kryptex
- 💶 Affichage des estimations en **€ ou $**
- 📊 Affichage du **TOTAL BENCH**
- ⚡ Affichage du **TOTAL ACTUEL basé sur le hashrate réel**
- ⚡ Affichage en direct du **hashrate et de la consommation CPU/GPU**
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

Téléchargez la dernière version depuis les Releases GitHub.

Exemple pour la **V2.0** :

```bash
cd /home/user

wget https://github.com/Dorian-360/Kryptex-autoswitch/releases/download/v2.0/kryptex-autoswitch

chmod +x kryptex-autoswitch
```

Puis lancez AutoSwitch :

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1
```

> `--cpu 32` correspond au nombre maximum de threads CPU autorisés.

> `--gpu 1` active le minage GPU. Tous les GPU compatibles détectés peuvent être utilisés.

---

## 🔑 3. Identifiant Kryptex

Au premier lancement, le script vous demande votre **Mining Username Kryptex**.

Il ressemble à ceci :

```text
krxX3QD88J
```

Entrez uniquement votre identifiant `krx...`.

Le nom de votre machine est automatiquement ajouté comme nom de worker.

Par exemple :

```text
krxX3QD88J.9950x-01
```

La configuration est ensuite enregistrée automatiquement pour les prochains lancements.

---

## 💱 4. Conversion automatique des gains

AutoSwitch peut miner différentes cryptomonnaies en fonction de leur rentabilité.

**Vous n'avez rien à convertir manuellement.**

En utilisant votre **Mining Username Kryptex**, les monnaies minées sont envoyées vers Kryptex et les gains sont gérés par votre compte Kryptex.

```text
AutoSwitch
     ↓
Recherche la monnaie la plus rentable
     ↓
CPU et GPU minent automatiquement
     ↓
Kryptex reçoit les gains
     ↓
Gestion / conversion par Kryptex
     ↓
Solde crédité sur votre compte
```

AutoSwitch peut donc passer automatiquement d'une monnaie à une autre sans modifier votre configuration.

---

# ⚙️ 5. Commandes

## 🖥️ CPU + GPU

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1
```

Active le CPU avec un maximum de 32 threads ainsi que le ou les GPU détectés.

---

## 🎮 GPU uniquement

```bash
sudo ./kryptex-autoswitch --cpu 0 --gpu 1
```

---

## 🧠 CPU uniquement

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 0
```

---

## ⚡ Mode rendement CPU

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1 --cpu-efficient
```

Le mode `--cpu-efficient` teste différents nombres de threads CPU afin de déterminer automatiquement celui qui offre le meilleur rapport :

```text
Hashrate / consommation électrique
```

Exemple :

```text
 4 threads :  3.35 kH/s │  56.9 W │  58.9 H/s/W
 8 threads :  6.65 kH/s │  77.6 W │  85.6 H/s/W
12 threads :  9.87 kH/s │  97.5 W │ 101.3 H/s/W
16 threads : 13.04 kH/s │ 116.8 W │ 111.7 H/s/W
20 threads : 15.48 kH/s │ 129.9 W │ 119.2 H/s/W
24 threads : 17.89 kH/s │ 138.9 W │ 128.8 H/s/W
28 threads : 20.26 kH/s │ 148.7 W │ 136.2 H/s/W
32 threads : 22.26 kH/s │ 159.4 W │ 139.6 H/s/W
```

Dans cet exemple, AutoSwitch sélectionnera automatiquement :

```text
32 threads
22.26 kH/s
159.4 W
139.6 H/s/W
```

Le résultat est enregistré localement afin de ne pas refaire cette recherche à chaque lancement.

La valeur de `--cpu` reste la **limite maximale autorisée**.

Par exemple :

```bash
--cpu 24 --cpu-efficient
```

permet à AutoSwitch de rechercher le meilleur rendement jusqu'à **24 threads maximum**.

---

## 🎮 Désactiver la gestion automatique des profils GPU

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1 --no-oc
```

Cette option désactive l'application automatique des profils GPU.

Le minage et l'AutoSwitch continuent de fonctionner normalement, mais AutoSwitch ne modifie pas automatiquement les paramètres GPU.

---

## 🔄 Refaire les benchmarks

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1 --rebench
```

`--rebench` force la reconstruction des benchmarks au lieu de réutiliser les résultats enregistrés.

Avec le mode rendement CPU :

```bash
sudo ./kryptex-autoswitch --cpu 32 --gpu 1 --cpu-efficient --rebench
```

---

## 📋 Résumé des arguments

| Argument | Fonction |
|---|---|
| `--cpu N` | Nombre maximum de threads CPU |
| `--gpu 1` | Active le minage GPU |
| `--gpu 0` | Désactive le minage GPU |
| `--cpu-efficient` | Recherche automatiquement le meilleur rendement CPU |
| `--no-oc` | Désactive la gestion automatique des profils GPU |
| `--rebench` | Force la reconstruction des benchmarks |

---

# 🎮 6. Gestion automatique des GPU

AutoSwitch V2.0 peut gérer plusieurs GPU installés dans la même machine.

Exemple :

```text
GPU0: NVIDIA GeForce RTX 3090
GPU1: NVIDIA GeForce RTX 3080
```

Chaque GPU est identifié séparément afin de pouvoir lui appliquer un profil adapté.

Les profils sont conservés localement pour éviter de rechercher les mêmes informations à chaque démarrage.

Lorsqu'un profil exact n'est pas disponible, AutoSwitch peut utiliser un profil de secours compatible plutôt que d'appliquer arbitrairement un réglage agressif.

Les profils instables détectés peuvent également être évités afin de limiter les risques de plantage du pilote GPU.

> L'overclocking et l'undervolting dépendent fortement du modèle de carte, de son refroidissement, de son alimentation et de la qualité de la puce. Surveillez toujours les températures et la stabilité de votre matériel.

---

# 📊 7. Affichage en temps réel

AutoSwitch affiche notamment :

- la rentabilité de chaque monnaie compatible ;
- la monnaie sélectionnée pour le CPU ;
- la monnaie sélectionnée pour le GPU ;
- le hashrate CPU actuel ;
- le hashrate GPU actuel ;
- la consommation CPU actuelle ;
- la consommation GPU actuelle ;
- les gains estimés en **€ ou $** ;
- les estimations par jour, 30 jours et année.

Exemple :

```text
             KRYPTEX AUTOSWITCH-POUSSIN V2.0  •  Gains en € (EUR)

┌───────────────────── CPU ──────────────────────┐   ┌───────────────────── GPU ──────────────────────┐
│ ▶ XMR        0.8091 €/j  22.24 kH/s  162W     │   │ ▶ PRL        4.1688 €/j  147.61 TH/s  234W     │
│   XTM-RX     0.6895 €/j                        │   │   QTC        3.3807 €/j                        │
│   XEL        0.6782 €/j                        │   │   RVN        0.5592 €/j                        │
│   ZEPH       0.4592 €/j                        │   │   CFX        0.5573 €/j                        │
└────────────────────────────────────────────────┘   │   XEL        0.3945 €/j                        │
                                                     │   ERG        0.3841 €/j                        │
                                                     │   NEXA       0.3078 €/j                        │
                                                     │   IRON       0.2582 €/j                        │
                                                     │   XNA        0.1122 €/j                        │
                                                     │   ETHW       0.0929 €/j                        │
                                                     └────────────────────────────────────────────────┘
```

---

## 📊 TOTAL BENCH

Le **TOTAL BENCH** correspond à l'estimation obtenue à partir des hashrates enregistrés pendant les benchmarks.

```text
┌─────────────────────────────── TOTAL BENCH ────────────────────────────────┐
│  CPU: XMR        0.8091 €/j   +   GPU: PRL        4.1688 €/j               │
│  TOTAL : 4.9779 €/jour   │   149.34 €/30j   │   1816.93 €/an               │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## ⚡ TOTAL ACTUEL

Le **TOTAL ACTUEL** utilise le hashrate réellement produit par les mineurs en cours d'exécution.

Il affiche également la consommation électrique mesurée du CPU et du GPU.

```text
┌─────────────────────────────── TOTAL ACTUEL ───────────────────────────────┐
│  CPU: XMR      22.24 kH/s   162W   →   0.8086 €/j                          │
│  GPU: PRL      147.61 TH/s  234W   →   3.3545 €/j                          │
│  TOTAL : 4.1631 €/jour   │   124.89 €/30j   │   1519.53 €/an               │
└────────────────────────────────────────────────────────────────────────────┘
```

Cela permet de comparer immédiatement :

```text
Benchmark théorique
        ↓
Hashrate réellement obtenu
        ↓
Consommation réelle
        ↓
Rentabilité actuelle estimée
```

> La consommation affichée correspond aux mesures accessibles au système pour le CPU/GPU. Elle ne représente pas nécessairement la consommation totale de la machine à la prise.

---

# 💾 8. Conservation des benchmarks et profils

AutoSwitch conserve localement les informations nécessaires dans :

```text
/home/user/kryptex-miners/
```

On peut notamment y retrouver :

```text
config.json
benchmarks-v5.2.json
cpu-efficiency.json
oc-cache.json
versions-v5.2.json
miners/
logs/
```

Cela permet à AutoSwitch de réutiliser les résultats existants au démarrage.

Ainsi, si le matériel et la version du mineur n'ont pas changé :

```text
✓ Profil rendement CPU chargé depuis le cache
✓ Tous les benchmarks sont valides pour les versions de mineurs installées
```

AutoSwitch peut alors démarrer le minage sans refaire inutilement tous les benchmarks.

---

# 🔄 9. Mises à jour des mineurs

AutoSwitch gère automatiquement les mineurs nécessaires aux différents algorithmes.

Le script peut :

- détecter les versions installées ;
- rechercher de nouvelles versions ;
- télécharger automatiquement les nouvelles versions ;
- conserver les benchmarks lorsque la version du mineur n'a pas changé ;
- invalider les benchmarks concernés lorsqu'un mineur est mis à jour ;
- refaire uniquement les benchmarks nécessaires.

Le contrôle des mises à jour est également effectué périodiquement pendant le fonctionnement d'AutoSwitch.

S'il n'y a aucune mise à jour :

**le minage continue normalement sans interruption.**

---

# 🔄 10. Fonctionnement de l'AutoSwitch

```text
Chargement des benchmarks
          ↓
Chargement des profils GPU
          ↓
Recherche éventuelle du rendement CPU
          ↓
Calcul de la rentabilité
          ↓
Sélection CPU + GPU
          ↓
Application des profils GPU
          ↓
Démarrage des mineurs
          ↓
Lecture du hashrate et de la consommation
          ↓
Actualisation de la rentabilité toutes les 60 s
          ↓
Une monnaie devient suffisamment plus rentable ?
          │
          ├── NON → le minage continue
          │
          └── OUI → changement automatique
```

Le CPU et le GPU sont gérés **indépendamment**.

Le CPU peut donc miner une monnaie pendant que le GPU en mine une autre.

---

# ❤️ Soutenir Kryptex AutoSwitch Linux

Kryptex AutoSwitch Linux prélève :

# **0 % de frais supplémentaires**

Aucun pourcentage supplémentaire n'est prélevé par AutoSwitch sur votre minage.

Si vous souhaitez soutenir le développement du projet, vous pouvez créer votre compte Kryptex avec mon lien de parrainage :

https://www.kryptex.com/?ref=95ac8ffd

Cela permet de soutenir le développement du projet sans ajouter de frais supplémentaires au script.

**Merci et bon minage ! ⛏️**

---

# ⚠️ Avertissement

**Kryptex AutoSwitch Linux est un projet communautaire non officiel, indépendant et non affilié à Kryptex.**

Les estimations de rentabilité peuvent évoluer rapidement selon :

- le cours des cryptomonnaies ;
- la difficulté des réseaux ;
- les performances du matériel ;
- les frais propres aux logiciels de minage utilisés ;
- les données fournies par Kryptex et les pools ;
- les variations du hashrate réel.

Les profils GPU automatiques ne garantissent pas la stabilité de toutes les cartes. Deux GPU du même modèle peuvent avoir un comportement différent.

Surveillez notamment :

- les températures GPU ;
- la température mémoire lorsque celle-ci est disponible ;
- la consommation ;
- les erreurs du pilote ;
- les shares rejetées ;
- la stabilité générale de la machine.

Les valeurs affichées par AutoSwitch sont des **estimations** et ne garantissent pas les revenus réellement obtenus.
