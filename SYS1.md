<style>
  body{
      line-height: 110%;
  }
</style>

## Fiche de Révision - Structures de Contrôle dans le Shell

### 0. Prérequis
  - **Single Quotes (' ') :** Préservent littéralement le texte, sans interprétation. 
  - **Double Quotes (" ") :** Permettent l'interprétation du texte.
  - **Back Quotes (\` \`) :** Exécutent une commande à l'intérieur et substituent le résultat. Préférer l'utilisation de `$(  )`
  - **Opérations arithmétiques $(( )) :** est remplacé par les résultats de l'expression arithmétique évaluée. L'utilisation des `$` pour les variable n'est pas nécéssaire.
  - **Caractères inconnus (*, ?) :** * s'ignifie n'importe quelle suite de caractère et ?, un et un seul caractère
  - **Pipe (COMMANDE | COMMANDE) :** Passe la sortie standard de la 1ère commande dans l'entrée standard de la 2ème commande.
  - **Redirection (COMMANDE <, >, 2> FICHIER) :** > Redirige la sortie d'une commande vers un fichier. < Redirige le contenu d'un fichier dans l'entrée d'une commande. 2> Redirige les erreurs de la commandes dans le fichier.

### 1. Variables dans le Shell
  - `variable="valeur"` : Définit une variable.
  - `$variable` : Accède à la valeur d'une variable.
  - **Environnement :**
    - `env`: Permet de les consulter
    - `$SHELL`: indique quel type de shell est en cours d'utilisation (sh, bash, ksh…) ;
    - `$PATH`: Liste de répertoire contenant les exécutables. Ajout avec `export PATH=$PATH:DIR`
    - `$EDITOR`: Editeur de texte shell par défaut
    - `$HOME`: Position du dossier home
    - `$PWD`: Dossier actuel
    - `$OLDPWD`: Dossier précédent
  - **Arguments du script**
    - `$#` : Le nombre d'arguments
    - `$@` : Tout les arguments passés à la fonction
    - `$0` : Nom du scipt
    - `$n` : Argument n, de 0 à 9


### 2. Structures de Test
  - **If :**
  ```bash
  if [ condition ]; then 
     # Instructions à exécuter si condition rempli ;;
  elif [ condition ]; then
     # Instructions si condition rempli ;;
  else
     # Si aucune condition précédente n'est rempli
  fi #Termine une structure de test.
  ```

  - **Case :**
  ```bash
  case expression in
    motif1 )
      # Instructions à exécuter si expression correspond à motif1 ;;
    * )
      # Instructions par défaut si aucune correspondance ;;
  esac
  ```
### 3. Les Comparaisons
- Condition1 **OU** Condition2: `[ condition1 ] || [ condition2 ]`
- Condition1 **ET** Condition2: `[ condition1 ] && [ condition2 ]`

- **Chaînes :**
  - `==` : Égal.
  - `!=` : Différent.
  - `-z` : Chaine vide
  - `-n` : Chaine non vide

- **Numérique :**
  - `-eq` : Égal.
  - `-ne` : Différent.
  - `-lt` : Inférieur à.
  - `-le` : Inférieur ou égal à.
  - `-gt` : Supérieur à.
  - `-ge` : Supérieur ou égal à.

- **Fichiers :**

  - `-e fichier` : Vrai si le fichier existe.
  - `-d repertoire` : Vrai si le fichier est un répertoire.
  - `-f fichier` : Vrai si le fichier est un fichier régulier.
  - `-L fichier` : Vrai si le fichier est un lien.
  - `-r fichier` : Vrai si le fichier est lisible.
  - `-w fichier` : Vrai si le fichier est modifiable.
  - `-x fichier` : Vrai si le fichier est executable.
  - `-s fichier` : Vrai si le fichier a une taille supérieure à zéro.
  - `fichier -nt fichier` : Plus récent que
  - `fichier -ol fichier` : Plus vieux que

### 4. Structures de Boucle

- **Boucle For :**
    ```bash
    for variable in liste; do
      # Instructions à exécuter
    done
    ```

- **Boucle While :**
    ```bash
    while [ condition ]; do
      # Instructions à exécuter
    done
    ```

- **Boucle Until :**
    ```bash
    until [ condition ]; do
      # Instructions à exécuter
    done
    ```

### 5. Echo et Read

- **Echo :**
  - `echo "texte"` : Affiche du texte sur la sortie standard.
  - Options utiles :
    - `-e` : Interprète les caractères d'échappement.
    - **Les couleurs:**
      - `\e[31m` : Rouge
      - `\e[32m` : Vert
      - `\e[33m` : Jaune
      - `\e[34m` : Bleu
      - `\e[35m` : Magenta
      - `\e[36m` : Cyan
      - `\e[37m` : Blanc
      - `\e[41m` : Fond Rouge
      - `\e[42m` : Fond Vert
      - `\e[43m` : Fond Jaune
      - `\e[44m` : Fond Bleu
      - `\e[45m` : Fond Magenta
      - `\e[46m` : Fond Cyan
      - `\e[47m` : Fond Blanc
      - `\e[1m` : Gras
      - `\e[4m` : Souligné
      - `\e[7m` : Inverser les couleurs (texte sur fond coloré)
      - `\e[0m` : Réinitialise les paramètres de couleur et de style à la valeur par défaut.
      - Affiche le texte "Hello World" en rouge avec un fond vert :
        ```bash
        echo -e "\e[31m\e[42mHello World\e[0m"
        ```
      - Affiche du texte gras et souligné en jaune :
        ```bash
        echo -e "\e[1;4;33mHello\e[0m"
        ```

- **Read :**
  - `read [options] variablen` : Lit une entrée de l'utilisateur et la stocke dans une variable.
  - Options utiles pour `read` :
    - `-p "prompt"` : Affiche un message d'invite.
    - `-s` : Lit en mode silencieux (utile pour les mots de passe).
    - `-n` : Limiter le nombre de charactère.
    - `-t` : Limiter le temps pour saisir en secondes.


### 6. Commandes
  - **`sudo COMMANDE` - Exécute une commande avec des droits d'administrateur**
  - **`xargs COMMANDE` - Passe l'entrée standard en tant qu'argument de la commande**
    - `-n` : Nombre d'arguments à utiliser à la fois.
    - `-I` : Remplace les occurrences spécifiées dans la commande.
  - **`ls` - Liste les fichiers et répertoires**
     - `-l` : Affiche les détails en format long.
     - `-a` : Montre également les fichiers cachés.
     - `-R` : L'ensemble des fichiers, mêmes les sous-répertoires.
  - **`cd` - Change le répertoire courant**
     - `<répertoire>` : Change vers le répertoire spécifié.
     - `../` : Permet le retour en arrière
     - `/` : Désigne la racine
     - `~/` : Désigne la racine de l'utilisateur
  - **`cp, mv, rm` - Copie, déplace ou supprimer des fichiers ou des répertoires**
     - `-r` : Effectue l'opération récursivement pour les répertoires.
     - `-f` : Force la suppression sans confirmation.
  - **`cal` - Affiche le calendrier**
  - **`cat` - Concatène et affiche le contenu des fichiers**
     - `-s` : Ne retourne que les lignes non-vides
     - `-v` : Affichage des caractères non-imprimables
     - `-n` : Numérotation des lignes
  - **`nano FICHIER` - Éditeur de texte en mode terminal**
  - **`tree` - Affiche la structure d'arborescence des fichiers**
  - **`find DIR` - Recherche des fichiers dans un répertoire**
      - `-name` : Recherche par nom de fichier.
      - `-iname` : Recherche par nom de fichier sans tenir compte de la casse.
      - `-type` : Spécifie le type de fichier (fichier, répertoire, lien, etc.).
  - **`head, tail FICHIER` - Affiche les premières/dernières lignes d'un fichier**
      - `-n` : Nombre de lignes à afficher.
  - **`kill N` - Permet de 'tuer' le processus de PID N**
      - `-s` : Spécifier un signal: TERM (par défaut) peut être ignoré, mais pas KILL
  - **`ps` - Affiche les processus actifs**
  - **`pstree N` - Affiche l'arborescence des processus à partir de N**
  - **`grep FICHIER` - Recherche une chaine dans un fichier ou l'entrée standard, retourne les lignes**
      - `-i` : Ignorer la casse.
      - `-l` : Retourne le nom du fichier
      - `-v` : Retourne les lignes qui ne contiennent pas
  - **`wc FICHIER` - Compte le nombre de lignes, mots et caractères d'un fichier**
      - `-l` : Compte le nombre de lignes.
      - `-w` : Compte le nombre de mots.
      - `-m` : Compte le nombre de caractères.
  - **`tr CHAINE1 CHAINE2` - Transpose ou supprime des caractères**
  - **`touch NOM` - Crée un nouveau fichier**
  - **`unzip FICHIER` - Décompresse les fichiers ZIP**
  - **`cut CHAINE` - Coupe des portions de texte de chaque ligne d'un fichier**
      - `-f` : Spécifie les champs à extraire.
      - `-d` : Spécifie le délimitateur de ce qui est à découpé
  