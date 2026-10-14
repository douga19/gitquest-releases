<h1>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/gitquest-logo-dark.svg">
    <img alt="gitquest" src="assets/gitquest-logo-light.svg" height="40">
  </picture>
</h1>

gitquest permet d'apprendre Git en jouant, avec le **vrai** Git. Il prépare des
dépôts d'exercice, observe ce que tu fais dans ton terminal, donne un retour
immédiat et vérifie le résultat. Ce dépôt contient uniquement les versions
téléchargeables du programme.

Cours associé : <https://douga19.github.io/efrei-git/>

## Prérequis

- **Git 2.28 ou plus récent** (vérifie avec `git --version`).
  Si Git n'est pas installé : <https://git-scm.com/downloads> (sous Windows, il installe aussi Git Bash).
- Sur Windows, **Git Bash** (installé avec [Git for Windows](https://gitforwindows.org/)) :
  c'est le terminal du cours.

gitquest est un seul fichier exécutable : il n'y a rien d'autre à installer.

## Télécharger

Ouvre la page de la dernière version :
<https://github.com/douga19/gitquest-releases/releases/latest>

Dans la section *Assets*, télécharge l'archive qui correspond à ton système :

| Système | Archive |
|---|---|
| Windows (PC classique, x64) | `gitquest_<version>_windows_amd64.zip` |
| Windows sur processeur ARM (Surface Pro X, Snapdragon…) | `gitquest_<version>_windows_arm64.zip` |
| macOS, puce Apple (M1, M2, M3…) | `gitquest_<version>_darwin_arm64.tar.gz` |
| macOS, processeur Intel | `gitquest_<version>_darwin_amd64.tar.gz` |
| Linux (x64) | `gitquest_<version>_linux_amd64.tar.gz` |
| Linux (ARM) | `gitquest_<version>_linux_arm64.tar.gz` |

Sur macOS, menu Pomme → *À propos de ce Mac* indique « Puce Apple » ou « Intel ».

## Installer

Le but est de pouvoir taper `gitquest` depuis n'importe quel dossier.

### Windows (Git Bash)

1. Décompresse l'archive (clic droit → *Extraire tout*).
2. Copie `gitquest.exe` dans le dossier `~/bin`. Dans Git Bash :
   ```sh
   mkdir -p ~/bin
   cp <chemin vers gitquest.exe> ~/bin/
   ```
   Remplace `<chemin vers gitquest.exe>` par l'emplacement du fichier extrait,
   par exemple `~/Downloads/gitquest_v0.1.0_windows_amd64/gitquest.exe`.
3. Ferme puis rouvre Git Bash : il ajoute `~/bin` au PATH automatiquement.

### macOS et Linux

```sh
tar -xzf gitquest_*_darwin_arm64.tar.gz      # adapte le nom de l'archive
mkdir -p ~/.local/bin
mv gitquest_*/gitquest ~/.local/bin/
```

Si `~/.local/bin` n'est pas déjà dans ton PATH, ajoute cette ligne à la fin de
`~/.zshrc` (macOS) ou `~/.bashrc` (Linux), puis rouvre le terminal :

```sh
export PATH="$HOME/.local/bin:$PATH"
```

## Premier lancement : avertissement de sécurité

gitquest n'est pas signé numériquement. Au premier lancement, le système
indique qu'il ne connaît pas l'éditeur : c'est attendu, et cela ne se produit
qu'une fois.

- **Windows (SmartScreen)** : si le message « Windows a protégé votre
  ordinateur » apparaît, clique sur *Informations complémentaires* puis
  *Exécuter quand même*.
- **macOS (Gatekeeper)** : si macOS refuse d'ouvrir gitquest, retire la marque
  de quarantaine posée par le navigateur :
  ```sh
  xattr -d com.apple.quarantine ~/.local/bin/gitquest
  ```
  Tu peux aussi passer par *Réglages Système* → *Confidentialité et sécurité*
  → *Ouvrir quand même*.

## Démarrer

```sh
gitquest version      # doit afficher gitquest v…
gitquest              # ouvre le tableau de bord dans le navigateur (Ctrl+C pour l'arrêter)
gitquest niveau       # démarre le niveau suivant et indique le dossier où aller
```

Les instructions détaillées, avec les solutions aux problèmes courants, sont
dans [INSTALL.md](INSTALL.md).
