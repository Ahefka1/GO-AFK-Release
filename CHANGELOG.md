# Changelog

Historique des versions **GO-AFK** publiées sur ce dépôt.

---

## [1.2.0] — 2026-04-25

Correctif ciblé du système de mise à jour en ligne.

### Correctifs

- Flux d’update durci pour éviter les erreurs de thread UI pendant l’installation.
- Fermeture de l’application effectuée via le dispatcher UI (thread-safe).
- Script updater externe renforcé avec retries de copie avant relance, pour mieux gérer les verrous temporaires.
- Plus de tentative de manipulation risquée du process courant pendant sa propre mise à jour.

### Publication

- Version affichée dans l’application : **1.2.0**.
- Build release préparé en **single-file self-contained** (`GO-AFK.exe`).

---

## [1.1] — 2026-04-25

Mise à jour UI/diagnostic et préparation release.

### Nouveautés et améliorations

- Dashboard retravaillé : KPI GPU simplifié ajouté, KPI fuseau retiré, carte disque simplifiée (`utilisé/total` en valeurs only).
- Tuiles dashboard harmonisées : descriptions unifiées, suppression des mentions `Section...` / `Onglet...`, retrait du badge `(WIP)` sur Diagnostic.
- Panneau **Exécution** refondu : cartes compactes, détail brut en dropdown par action, meilleure lisibilité globale.
- Statuts d’actions stabilisés : passage en `OK/ERREUR` plus cohérent (fin d’action, cas speedtest et SMART inclus).
- Module réseau : sortie ping formatée proprement (encodage lisible en français).
- Action rapide `Resync time` : popup dédiée au standard GO-AFK (dark, croix `✕`, sans bouton Fermer natif).
- Processus suspects : popup complète avec scan manuel, détails process (PID/chemin/commande/signature), VirusTotal, Kill avec confirmation.
- Diagnostic système : correction DISM (encodage + statut), et détail TPM enrichi avec version (aligné infos système).
- Recherche universelle : aliases étendus + amélioration UI (cards/badges/empty state/chips raccourcis).

### Publication

- Version affichée dans l’application : **1.1**.
- Build release préparé en **single-file self-contained** (`GO-AFK.exe`).

---

## [1.0.0] — 2026-04-16

Première release publique.

### Contenu principal

- Application bureau **WPF** ciblant **.NET 8** (Windows), déploiement possible en **exe unique self-contained**.
- **Interface** : thème sombre unifié, navigation par tuiles et vues dédiées, journal d’activité.
- **Encodage & console** : appels système via **PowerShell** avec **UTF-8** et **`-EncodedCommand`** lorsque nécessaire (caractères français, chemins).
- **winget** : résolution du binaire **`winget.exe`**, **`--scope machine`** lorsque applicable, fenêtres pour recherche, désinstallation, historique et winget.run.
- **Modules** : tableau de bord, réseau, nettoyage, réparation (dont AdwCleaner si présent dans `tools\`), disques & pilotes, logiciels, sauvegarde profil, performances, sécurité, diagnostic système (filtres OK / Warn / Error, détail formaté, recontrôle par section — parties du module en **WIP**), post-install, informations système, export journal.

### Mises à jour & publication

- **Mise à jour depuis l’application** : vérification au démarrage via l’API GitHub Releases (`Ahefka1` / `GO-AFK-Release` embarqués — distribution **exe seul**, sans JSON obligatoire à côté du binaire).
- **Assets release** : `GO-AFK.exe` + **`update.json`** (`version`, `sha256` du exe publié, `notes` cumulatives). Modèle : `release_update.example.json`.
- **Remplacement** : téléchargement, contrôle SHA256, script PowerShell puis redémarrage ; fenêtres sombres (disponible / notes).
- **Notes de version** : lien **Détail de version** dans le pied de page ; changelog **embarqué** dans l’exe tant qu’aucune note distante n’est en cache ; après mise à jour, affichage des notes issues de `update.json`.
- **Robustesse** : absence de release GitHub (HTTP 404) gérée sans erreur bloquante dans le journal.

### Technique

- Cible : **.NET 8**, **Windows** (`net8.0-windows`), WPF ; version affichée **1.0.0** (pied de page dynamique depuis l’assembly).
- Manifeste application : exécution **avec élévation** (`requireAdministrator`) pour les opérations système — invite UAC possible au lancement.
- Outils tiers optionnels : répertoire `tools\` (SDIO, CrystalDiskInfo portable, smartctl, AdwCleaner, etc.) — à fournir avant distribution si vous les embarquez.
- Fichier embarqué `Resources/EmbeddedChangelog.md` dans le projet source (à tenir aligné avec ce CHANGELOG lors des prochaines releases).

---

## Format des versions

- Numérotation : `MAJOR.MINOR` ou `MAJOR.MINOR.PATCH` (ex. `1.0`, `1.0.0`, `1.1.0`).
- Les tags Git des releases peuvent suivre la forme `v1.0`, `v1.0.0`, etc.
