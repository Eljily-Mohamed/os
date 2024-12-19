# OS Lab Project  

## Introduction  
Le but de ce projet est d’explorer les fondements d’un système d’exploitation multitâche simple pour une architecture ARM.
La cible matérielle utilisée est la **carte LPC55S69-EVK**, qui s’appuie sur le **microcontrôleur LPC55S69** de NXP. Le projet se concentre sur le **Core 0 Cortex-M33** pour développer et tester un système d’exploitation personnalisé.  

Le logiciel s’organise en deux parties principales :  
1. **Code applicatif** (mode *Thread unprivileged*) :  
   - Permet l’exécution de plusieurs tâches (*processus*) en pseudo-parallèle.  
   - Fournit l’accès aux services du système d’exploitation (création de tâches, sémaphores, etc.) via des **appels systèmes** (*SVC - SuperVisor Call*).  
   - Autorise la gestion des interruptions.  

2. **Système d’exploitation** (mode *Handler privileged* et *Thread unprivileged*) :  
   - **Noyau** :  
     - Gère les tâches et les sémaphores.  
     - Réalise la commutation des tâches via une interruption du **timer système** (mode *round-robin*) ou sur des événements (sémaphores ou temporisation).  
     - Assure qu’une seule tâche utilise le processeur à un instant donné.  
     - Les appels systèmes (*SVC*) sont non interruptibles par les **IRQ périphériques**.  
   - **Drivers** :  
     - Permettent la communication entre l’application et le matériel via une interface standard.  
     - Exploitent les outils de synchronisation du noyau (comme les sémaphores) pour un fonctionnement robuste, que les périphériques fonctionnent sur interruption ou non.  

---

## Matériel Utilisé  
- **Carte cible** : LPC55S69-EVK  
- **Périphériques intégrés** :  
  - **USART** : Communication série pour débogage et interface terminal.  
  - **Accéléromètre** : Pour capturer les données d’accélération en temps réel.  
  - **Carte SD** : Gestion d’un système de fichiers virtuel (FATFS).  

---

## Fonctionnalités Implémentées  
1. **Tâches applicatives** :  
   - Création et gestion de plusieurs tâches s’exécutant en pseudo-parallèle.  
   - Support des appels systèmes (*SVC*) pour accéder aux fonctionnalités du noyau.  

2. **Synchronisation et Communication** :  
   - Gestion des **sémaphores** pour la communication entre tâches et périphériques.  
   - Synchronisation des périphériques fonctionnant sur interruption.  

3. **Commutation de Tâches** :  
   - Planification en mode **tourniquet** (*round-robin*).  
   - Commutation basée sur des événements système (sémaphores, temporisation).  

4. **Drivers** :  
   - Interface standardisée pour les périphériques (USART, accéléromètre, carte SD).  

5. **Système de Fichiers** :  
   - Gestion des fichiers sur carte SD avec FATFS.  

---

## Instructions pour l’Utilisation  
1. **Configuration Matérielle** :  
   - Connecter les périphériques (accéléromètre, carte SD) à la carte LPC55S69-EVK.  
   - Configurer la communication USART avec un PC pour le débogage.  

2. **Compilation et Tests** :  
   - Sélectionnez le test souhaité dans `main.c` en définissant un label (`#define MAIN_EXx`).  
   - Compiler et flasher le code sur la carte cible.  

3. **Validation des Résultats** :  
   - Utilisez un terminal série (e.g., PuTTY) pour surveiller les sorties et les logs.  
   - Vérifiez les interactions avec les périphériques connectés.  

---

## Labels Disponibles dans `main.c`  
- **`MAIN_TEST`** : Vérifie un appel système simple.  
- **`MAIN_EX1`** : Création de la première tâche et changement de tâche.  
- **`MAIN_EX2`** : Multi-tâches avec exécution d’un même code.  
- **`MAIN_EX3`** : Test des sémaphores.  
- **`MAIN_EX4`** : Utilisation des sémaphores comme mutex.  
- **`MAIN_EX5`** : Fonction de temporisation.  
- **`MAIN_EX6`** : Exécution de deux tâches temporisées.  
- **`MAIN_EX7`** : Test de terminaison d’une tâche.  
- **`MAIN_EX8`** : Interface de fichiers virtuels.  
- **`MAIN_EX9`** : LED RGB comme périphérique.  
- **`MAIN_EX10`** : Bouton utilisateur avec gestion d’interruptions.  
- ---- 
---

## Licence  
Ce projet est sous licence MIT. Consultez le fichier `LICENSE` pour plus d'informations.  
