# Changelog

Historique des versions **GO-AFK** publiées sur ce dépôt.

---

## [1.0.0] — 2026-04-16

Première release publique.

### Contenu principal

- Application bureau **WPF** ciblant **.NET 8** (Windows), déploiement possible en **exe unique self-contained**.
- **Interface** : thème sombre unifié, navigation par tuiles et vues dédiées, journal d’activité.
- **Encodage & console** : appels système via **PowerShell** avec **UTF-8** et **`-EncodedCommand`** lorsque nécessaire (caractères français, chemins).
- **winget** : résolution du binaire **`winget.exe`**, **`--scope machine`** lorsque applicable, fenêtres pour recherche, désinstallation, historique et winget.run.
- **Modules** : tableau de bord, réseau, nettoyage, réparation (dont AdwCleaner si présent dans `tools\`), disques & pilotes, logiciels, sauvegarde profil, performances, sécurité, diagnostic système (filtres OK / Warn / Error, détail formaté, recontrôle par section — parties du module en **WIP**), post-install, informations système, export journal.

### Technique

- Cible : **.NET 8**, **Windows** (`net8.0-windows`), WPF.
- Manifeste application : exécution **avec élévation** (`requireAdministrator`) pour les opérations système — invite UAC possible au lancement.
- Outils tiers optionnels : répertoire `tools\` (SDIO, CrystalDiskInfo portable, smartctl, AdwCleaner, etc.) — à fournir avant distribution si vous les embarquez.

---

## Format des versions

- Numérotation : `MAJOR.MINOR` ou `MAJOR.MINOR.PATCH` (ex. `1.0`, `1.0.0`, `1.1.0`).
- Les tags Git des releases peuvent suivre la forme `v1.0`, `v1.0.0`, etc.
