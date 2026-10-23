# Installer gitquest

gitquest est un seul fichier exécutable. Il n'y a rien d'autre à installer,
à part **Git 2.28 ou plus récent**.

## 0. Installer Git

Vérifie d'abord si Git est déjà installé : ouvre un terminal et tape
`git --version`. Si une version 2.28 ou plus récente s'affiche, passe à l'étape 1.

- **Windows** : télécharge l'installateur sur <https://git-scm.com/download/win>
  et lance-le en gardant les options proposées par défaut. Il installe aussi
  **Git Bash**, le terminal à utiliser avec gitquest.
- **macOS** : tape `git --version` dans l'application Terminal. Si Git n'est pas
  installé, macOS propose d'installer les « outils de ligne de commande » :
  accepte. (Avec [Homebrew](https://brew.sh) : `brew install git`.)
- **Linux** : `sudo apt install git` (Debian, Ubuntu) ou `sudo dnf install git`
  (Fedora).

Toutes les versions : <https://git-scm.com/downloads>. Une fois installé, ferme
puis rouvre le terminal et vérifie avec `git --version`.

## 1. Télécharger

Sur la page de la dernière version
(<https://github.com/douga19/gitquest-releases/releases/latest>),
télécharge l'archive qui correspond à ton système :

| Système | Archive |
|---|---|
| Windows (PC classique) | `gitquest_<version>_windows_amd64.zip` |
| Windows sur processeur ARM (Surface Pro X, Snapdragon…) | `gitquest_<version>_windows_arm64.zip` |
| macOS, puce Apple (M1, M2, M3…) | `gitquest_<version>_darwin_arm64.tar.gz` |
| macOS, processeur Intel | `gitquest_<version>_darwin_amd64.tar.gz` |
| Linux | `gitquest_<version>_linux_amd64.tar.gz` (ou `linux_arm64`) |

Sur macOS, menu Pomme → *À propos de ce Mac* : « Puce Apple » ou « Intel ».

Le fichier `SHA256SUMS` permet de vérifier que l'archive n'a pas été
modifiée (facultatif) : `sha256sum -c SHA256SUMS --ignore-missing`
(sur macOS : `shasum -a 256 -c SHA256SUMS --ignore-missing`).

## 2. Mettre gitquest dans le PATH

Le but : pouvoir taper `gitquest` depuis n'importe quel dossier.

### Windows

**Utilise Git Bash** (installé avec [Git for Windows](https://gitforwindows.org/)) :
c'est le terminal du cours, et c'est lui que Git utilise pour afficher les
messages de gitquest après tes commandes.

1. Décompresse l'archive (clic droit → *Extraire tout*).
2. Crée le dossier `bin` dans ton dossier personnel et copies-y `gitquest.exe`.
   Dans Git Bash :
   ```sh
   mkdir -p ~/bin
   cp <chemin vers gitquest.exe> ~/bin/
   ```
   Remplace `<chemin vers gitquest.exe>` par l'emplacement du fichier extrait,
   par exemple `~/Downloads/gitquest_v0.1.0_windows_amd64/gitquest.exe`.
3. Git Bash ajoute `~/bin` au PATH automatiquement : ferme puis rouvre Git Bash.

Pour utiliser gitquest aussi dans PowerShell ou l'invite de commandes, ajoute
le dossier au PATH de Windows : menu Démarrer → « Modifier les variables
d'environnement pour votre compte » → `Path` → *Modifier* → *Nouveau* →
`%USERPROFILE%\bin`.

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

## 3. Passer l'avertissement de sécurité (une seule fois)

gitquest n'est pas signé numériquement : au premier lancement, le système te
prévient qu'il ne connaît pas l'éditeur. C'est attendu.

### macOS (Gatekeeper)

Au premier lancement, macOS peut refuser d'ouvrir gitquest (« impossible de
vérifier le développeur » ou « Apple n'a pas pu confirmer… »). Deux solutions :

- dans le terminal, retire la marque de quarantaine posée par le navigateur :
  ```sh
  xattr -d com.apple.quarantine ~/.local/bin/gitquest
  ```
- ou bien : lance `gitquest` une fois, ferme le message, puis va dans
  *Réglages Système* → *Confidentialité et sécurité*, et clique sur
  *Ouvrir quand même* en face de gitquest. Relance `gitquest`.

### Windows (SmartScreen)

Si Windows affiche « Windows a protégé votre ordinateur », clique sur
*Informations complémentaires* puis *Exécuter quand même*. Si l'antivirus
bloque le fichier, tu peux aussi faire clic droit sur le `.zip` téléchargé →
*Propriétés* → cocher *Débloquer* → *OK*, avant de le décompresser.

## 4. Vérifier

```sh
gitquest version
```

doit afficher `gitquest v…`. Ensuite :

```sh
gitquest            # le tableau de bord dans le navigateur (Ctrl+C pour l'arrêter)
gitquest carte      # la carte des niveaux, dans le terminal
gitquest niveau     # démarre le premier niveau
```

## En cas de problème

- `gitquest: command not found` : le dossier n'est pas dans le PATH, ou le
  terminal n'a pas été rouvert.
- `Git introuvable` ou version trop ancienne : installe ou mets à jour Git.
- Pas de message de gitquest après `git commit` : lance `gitquest statut`
  depuis le dossier du niveau, cela réinstalle le lien avec Git. Cela arrive
  notamment si tu as déplacé `gitquest` après avoir commencé un niveau.
- Caractères bizarres (`←[32m`) dans l'invite de commandes de Windows :
  utilise Git Bash ou Windows Terminal, ou lance gitquest avec `--no-color`.
