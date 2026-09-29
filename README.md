# ⛏️ Kryptex AutoSwitch Linux

AutoSwitch non officiel pour miner sur les pools Kryptex sous **Ubuntu / Linux** avec sélection automatique de la monnaie la plus rentable pour le **CPU et le GPU**.

Le script effectue les benchmarks de votre matériel, récupère les données de rentabilité, puis bascule automatiquement le CPU et le GPU vers les monnaies les plus intéressantes.

> ⚠️ Projet communautaire non officiel. Ce script n'est pas développé, maintenu ou approuvé par Kryptex.

## ✨ Fonctionnalités

- AutoSwitch CPU et GPU
- Comparaison automatique de la rentabilité
- Vérification de la rentabilité toutes les 60 secondes
- Changement de monnaie si l'écart dépasse 5 %
- Confirmation avant changement pour éviter les switchs permanents
- Benchmark automatique du matériel
- Conservation des benchmarks entre les redémarrages
- Nouveau benchmark automatique lorsqu'un mineur est mis à jour
- Téléchargement et mise à jour automatique des mineurs
- Support CPU multi-thread
- Possibilité de désactiver complètement CPU ou GPU
- Affichage dynamique dans le terminal
- Gain CPU + GPU total
- Affichage des gains en EUR (€) ou USD ($)
- Arrêt propre avec `Ctrl+C`

## 🪙 Monnaies actuellement prises en charge

### CPU

- XMR — RandomX
- XTM-RX — RandomX
- ZEPH — RandomX
- XEL — XelisHash

### GPU

- PRL — PearlHash
- QTC — Quantus
- XEL — XelisHash
- CFX — Octopus
- ERG — Autolykos2
- IRON — FishHash
- RVN — KawPow
- XNA — KawPow
- NEXA — NexaPow
- ETHW — Ethash

La liste pourra évoluer avec les futures versions du script.

## 🖥️ Mineurs utilisés

Le script télécharge automatiquement les mineurs nécessaires :

- XMRig
- SRBMiner-MULTI
- Rigel
- lolMiner

Vous n'avez donc normalement pas besoin de les installer manuellement.

---

# 1. Créer un compte Kryptex

Si vous n'avez pas encore de compte Kryptex, vous pouvez vous inscrire avec mon lien :

👉 https://www.kryptex.com/?ref=95ac8ffd

**Le script ne prélève aucun frais supplémentaire : 0 % de frais pour moi sur votre minage.**

Si vous souhaitez soutenir le développement du script, vous pouvez simplement créer votre compte Kryptex via mon lien ci-dessus.

Les éventuels frais propres aux pools et aux logiciels de minage utilisés restent évidemment indépendants du script.

---

# 2. Trouver son identifiant Kryptex

Le script vous demandera votre **Mining Username Kryptex** lors du premier lancement.

Connectez-vous à votre compte Kryptex puis ouvrez :

**Profil → Mining Username**

Votre identifiant ressemble à :

```text
krxXXXXXXX
```

Par exemple :

```text
krxX3QD88J
```

⚠️ Il ne faut pas entrer le nom de votre machine.

Le script ajoute automatiquement le hostname Linux pour créer le worker :

```text
krxXXXXXXX.nom-du-pc
```

Par exemple, sur une machine appelée `9950x-01` :

```text
krxX3QD94R.9950x-01
```

Documentation officielle Kryptex :

https://pool.kryptex.com/fr/articles/account-mining-fr

---

# 3. Installation

Téléchargez `kryptex-autoswitch` puis placez-le dans :

```bash
/home/user/kryptex-autoswitch
```

Rendez le fichier exécutable :

```bash
cd /home/user
chmod +x kryptex-autoswitch
```

Puis lancez-le :

```bash
./kryptex-autoswitch --cpu 32 --gpu 1
```

Au premier lancement, le script vous demandera notamment :

```text
Identifiant Kryptex :
```

Entrez uniquement votre identifiant :

```text
krxXXXXXXX
```

Il vous demandera également la devise d'affichage :

```text
Devise d'affichage des gains

1. € EUR
2. $ USD

Choix [1/2] :
```

La configuration est ensuite conservée automatiquement.

---

# 4. Utilisation

## CPU + GPU

Exemple avec 32 threads CPU et GPU activé :

```bash
./kryptex-autoswitch --cpu 32 --gpu 1
```

## CPU uniquement

```bash
./kryptex-autoswitch --cpu 32 --gpu 0
```

## GPU uniquement

```bash
./kryptex-autoswitch --cpu 0 --gpu 1
```

## Limiter le CPU

Par exemple, utiliser seulement 16 threads :

```bash
./kryptex-autoswitch --cpu 16 --gpu 1
```

---

# 5. Forcer un nouveau benchmark

Normalement, il n'est pas nécessaire de refaire les benchmarks à chaque lancement.

Le script conserve les performances mesurées.

Pour forcer un nouveau benchmark :

```bash
./kryptex-autoswitch --cpu 32 --gpu 1 --rebench
```

Utilisez notamment cette option après :

- un overclock ;
- un undervolt ;
- un changement de GPU ;
- un changement de CPU ;
- une modification importante des réglages de puissance.

Le script peut également invalider automatiquement les benchmarks concernés lorsqu'une nouvelle version d'un mineur est installée.

---

# 6. Fonctionnement de l'AutoSwitch

Par défaut :

```text
Vérification : 60 secondes
Seuil : 5 %
Confirmations : 2
```

Le script recalcule périodiquement la rentabilité.

Il évite de changer de monnaie pour une différence minime et attend que l'amélioration soit suffisamment importante avant d'effectuer un switch.

Le CPU et le GPU sont gérés indépendamment.

Il est donc possible d'avoir par exemple :

```text
CPU → XMR
GPU → PRL
```

---

# 7. Tableau de bord

Une fois les benchmarks terminés, le terminal est nettoyé et affiche un tableau dynamique.

Exemple :

```text
                         KRYPTEX AUTOSWITCH

┌──────────────── CPU ────────────────┐   ┌──────────────── GPU ────────────────┐
│ ▶ XMR          0.84 €/jour          │   │ ▶ PRL          5.04 €/jour          │
│   XTM-RX       0.82 €/jour          │   │   QTC          4.34 €/jour          │
│   XEL          0.74 €/jour          │   │   CFX          0.41 €/jour          │
│   ZEPH         0.57 €/jour          │   │   XEL          0.37 €/jour          │
└─────────────────────────────────────┘   │   ERG          0.37 €/jour          │
                                          └─────────────────────────────────────┘

┌──────────────────────── TOTAL MINAGE ────────────────────────┐
│ CPU : XMR                         GPU : PRL                  │
│ TOTAL ESTIMÉ : 5.88 €/jour                                   │
└───────────────────────────────────────────────────────────────┘
```

Le symbole :

```text
▶
```

indique la monnaie actuellement minée.

Le tableau est actualisé automatiquement sans ajouter de nouvelles lignes à chaque vérification.

---

# 8. Arrêter le mineur

Utilisez :

```text
Ctrl+C
```

L'AutoSwitch arrête alors le benchmark éventuel ainsi que les processus de minage CPU et GPU.

---

# 9. Fichiers utilisés

Les mineurs, benchmarks et paramètres sont stockés dans :

```bash
/home/user/kryptex-miners/
```

La configuration utilisateur se trouve notamment dans :

```bash
/home/user/kryptex-miners/config.json
```

⚠️ Ne supprimez pas ce répertoire si vous souhaitez conserver vos benchmarks et votre configuration.

---

# ⚠️ Avertissement

Le minage de cryptomonnaies sollicite fortement CPU et GPU et peut augmenter :

- la consommation électrique ;
- les températures ;
- le bruit ;
- l'usure du matériel.

Surveillez les températures et la consommation de votre machine.

Les estimations de rentabilité sont indicatives et peuvent évoluer rapidement en fonction du cours des cryptomonnaies, de la difficulté réseau et des conditions des pools.

Ce projet est fourni sans garantie.

---

# ❤️ Soutenir le projet

Le script est proposé avec **0 % de frais supplémentaires prélevés par son auteur**.

Si le projet vous est utile et que vous souhaitez me soutenir, vous pouvez créer votre compte Kryptex avec mon lien :

👉 https://www.kryptex.com/?ref=95ac8ffd

Merci pour votre soutien et bon minage ! ⛏️
