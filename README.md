# Infrastructure Cybersécurité - Keylogger & Détection

> **Projet académique** - Module Programmation Réseaux  
> ENSA Khouribga | Janvier 2025  
> **Équipe de 5 personnes**

---

## Objectif

Infrastructure de cybersécurité complète avec simulation d'attaques et détection multicouche :
- Keylogger Python multithread (simulation attaque)
- Détection et supervision (pfSense, Wazuh EDR/XDR, Cowrie, Nagios)
- Dashboard Flask pour centralisation des alertes

---

## Technologies

- **Attaque simulée** : Python (threading, sockets, pynput)
- **Pare-feu** : pfSense (3 zones LAN/DMZ/WAN)
- **Honeypot** : Cowrie (SSH/Telnet)
- **Détection** : Wazuh EDR/XDR (architecture manager-agent)
- **Supervision** : Nagios 4.4.6
- **Dashboard** : Flask (Python)

---

## Équipe & Répartition

**Équipe de 5 personnes**

| Membre | Rôle principal |
|--------|---------------|
| **Wissal RHANDI** | **Wazuh EDR/XDR + Dashboard Flask** |
| Imne Essaber | Keylogger Python client-serveur |
| Farah Ressati | Configuration pfSense (firewall, NAT) |
| Ikram Mihfad | Honeypot Cowrie |
| Chaymae Rachid | Nagios + Documentation |

---

## Ma Contribution Spécifique (Wissal RHANDI)

### Déploiement Wazuh EDR/XDR

**Architecture manager-agent mise en place :**

- **Wazuh Manager** (machine dédiée) :
  - Installation et configuration du serveur central
  - Collecte et corrélation des logs de sécurité
  - Règles de détection personnalisées
  - Stockage et indexation des événements

- **Wazuh Agent** (DMZ - honeypot) :
  - Installation agent sur machine honeypot (ID 001, rhandi-virtual-machine)
  - Configuration pour monitoring SSH/Telnet
  - Remontée logs Cowrie vers le manager
  - Détection des tentatives d'intrusion en temps réel

**Configuration réalisée :**
- Intégration avec honeypot Cowrie pour analyse attaques
- Règles de détection : brute force SSH, commandes suspectes
- Corrélation événements multi-sources
- Collecte logs système et applicatifs

### Développement Dashboard Flask Custom

**Pourquoi Flask ?** Kibana (dashboard natif Wazuh) non accessible à cause des ressources limitées du lab.

**Dashboard développé en Python Flask :**
- **Statistiques temps réel** :
  - 251 alertes détectées
  - 8 IPs bloquées
  - 3 agents actifs
  
- **Visualisations** :
  - Timeline des événements de sécurité
  - Top IPs malveillantes
  - Types d'attaques détectées
  - Statut des agents connectés

- **Intégration** :
  - Connexion API Wazuh pour récupération données
  - Mise à jour automatique des métriques
  - Interface web responsive

### Tests & Intégration

- Tests détection : attaques brute force SSH avec Hydra
- Validation remontée logs Cowrie → Wazuh
- Vérification alertes et corrélation événements
- Documentation procédures d'installation

**Limitation identifiée :** Automatisation Wazuh ↔ pfSense non réalisée (pas d'API native pfSense pour blocage dynamique des IPs détectées par Wazuh)

---

## Fonctionnalités du Système

**Détection (Wazuh - ma partie) :**
- ✅ Monitoring temps réel des tentatives d'intrusion
- ✅ Détection brute force SSH/Telnet
- ✅ Analyse comportementale des commandes suspectes
- ✅ Corrélation multi-sources (Cowrie + système)
- ✅ Alertes automatiques

**Dashboard (Flask - ma partie) :**
- ✅ Visualisation 251 alertes détectées
- ✅ Liste des 8 IPs bloquées
- ✅ Statut 3 agents actifs
- ✅ Timeline des événements

**Système complet (équipe) :**
- Segmentation réseau (pfSense)
- Honeypot SSH/Telnet (Cowrie)
- Keylogger multithread (Python)
- Supervision infrastructure (Nagios)

---

## Documentation

**[Rapport de projet complet (PDF)](docs/rapport-projet.pdf)**

*Le rapport détaille l'architecture complète, les configurations Wazuh, le code du dashboard Flask, et les résultats de détection.*

---

## Compétences Acquises

**Cybersécurité :**
- Wazuh EDR/XDR (architecture manager-agent)
- Détection d'intrusions (SIEM)
- Corrélation d'événements de sécurité
- Analyse de logs d'attaques

**Développement :**
- Python Flask (dashboard web)
- API REST (intégration Wazuh)
- Visualisation de données de sécurité
- Interface responsive

**Systèmes :**
- Linux (Ubuntu Server)
- Architecture de sécurité multicouche
- Intégration honeypot ↔ SIEM
- Tests d'intrusion

**Collaboration :**
- Travail en équipe (5 personnes)
- Intégration multi-composants
- Documentation technique

---

## Contact

**Wissal RHANDI**
- 📧 wissalrhandi685@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/wissalrhandi)
- 📍 Khouribga, Maroc

