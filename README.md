# GO-AFK

**Suite d’outils Windows pour techniciens et power users** — maintenance, diagnostic, logiciels, sauvegarde et sécurité, avec une interface unique en thème sombre.

Ce dépôt sert à **publier les versions stables** et les notes de version. Le développement principal reste privé ; seuls les binaires et la documentation de publication sont exposés ici.

---

## Téléchargement

Les fichiers installables sont publiés dans l’onglet **Releases** du dépôt GitHub correspondant (URL du type `https://github.com/<compte>/<nom-du-depot>/releases`).

- Téléchargez la **dernière release** (build *self-contained* Windows x64 recommandé).
- Exécutez l’application **en tant qu’administrateur** lorsque Windows ou les actions le demandent (UAC).

---

## Prérequis

| Élément | Détail |
|--------|--------|
| Système | **Windows 10 ou 11** (x64) |
| Runtime | Aucun si vous utilisez le build **self-contained** (.NET inclus dans l’exécutable) |
| Droits | Nombreuses actions (winget, DISM, stratégies, pilotes) nécessitent une **élévation** |

---

## Fonctionnalités

Application **bureau native** (WPF, **.NET 8**) :

- **Tableau de bord** : raccourcis système, indicateurs (réseau, disque, charge…), accès aux modules.
- **Réseau** : interfaces, DNS, tests, débit (dont Ookla CLI si présent), réinitialisations courantes.
- **Nettoyage** : ciblage des dossiers temporaires et gros fichiers.
- **Réparation** : raccourcis vers outils Windows (SFC, DISM, MRT, dépanneurs…) et outils tiers optionnels dans `tools\` (ex. **AdwCleaner**).
- **Disques & pilotes** : SMART, CrystalDiskInfo portable, SDIO, benchmarks.
- **Logiciels** : catalogue logiciel, **winget** (PowerShell, chemin explicite, `--scope machine` où applicable), recherche, historique, fenêtres dédiées.
- **Sauvegarde** : profil utilisateur (robocopy), dossier de destination et nom personnalisables, contrôle d’espace.
- **Performances** : suivi CPU / RAM, stress test, processus suspects, rapport batterie si portable.
- **Sécurité** : pare-feu, Defender, TPM, BitLocker (actions directes), etc.
- **Diagnostic système** : collecte large (infos matériel, thermiques, disques, réseau, DISM, activation, PUP, etc.), avec détail par section.
- **Post Install** : séquence guidée (fuseau, icônes bureau, installations winget, associations par défaut, nettoyage), fenêtre dédiée en thème sombre.
- **Journal** : traçabilité des actions, export possible.

Les détails par version sont dans **[CHANGELOG.md](CHANGELOG.md)**.

---

## Avertissements

- Outil **à risque** si mal utilisé : sauvegardes, images système et prudence sur les actions destructrices.
- Certaines fonctionnalités dépendent d’outils **optionnels** placés dans le dossier `tools\` à côté de l’exécutable (voir documentation embarquée / build).
- L’auteur / les contributeurs **ne sont pas responsables** des dommages liés à l’usage du logiciel. **Utilisation à vos risques.**

---

## Problèmes connus & support

- Ouvrez une **issue** sur ce dépôt pour les bugs liés aux **releases publiées** (crash, lien mort, incohérence de version).
- Pour toute demande de fonctionnalité, précisez la version affichée dans l’application et votre édition de Windows.

---

## Pour les mainteneurs — après un `git push` vers GitHub

1. Créer le dépôt distant (vide ou avec ce README) et ajouter le remote :  
   `git remote add origin https://github.com/<compte>/GO-AFK-Release.git`
2. Pousser la branche : `git push -u origin main`
3. Dans **Releases** → **Create a new release** :
   - **Tag** : `v1.1`
   - **Titre** : ex. `GO-AFK 1.1`
   - **Description** : copier la section correspondante du **CHANGELOG.md**
   - Joindre l’artefact issu de  
     `dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true`
4. **Mise à jour automatique dans l’application** : joignez à la release au minimum :
   - **`GO-AFK.exe`** — binaire publié ;
   - **`update.json`** — manifeste (voir `release_update.example.json`) : `version`, `sha256` de **ce** `GO-AFK.exe` (64 hex minuscules), `notes` (Markdown ou texte **cumulatif**).
   Les utilisateurs n’ont **pas** besoin de fichier JSON à côté de l’exe : le dépôt GitHub est **embarqué** dans l’application. Un fichier optionnel `update_sources.json` ne sert qu’à surcharger owner/repo (fork / test).

---

*« La flemme est une fonctionnalité, pas un bug. »*
