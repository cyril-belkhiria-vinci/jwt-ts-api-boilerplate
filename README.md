# Boilerplate d'une RESTful API en TS offrant l'authentification et l'autorisation via JWT

## Comment l'utiliser ?
### Installation
- Si vous ne l'avez pas fait, vous pouvez cloner le repo associé au boilerplate pour initier votre application : `git clone https://github.com/e-vinci/jwt-api-boilerplate.git` ou `git clone https://github.com/e-vinci/jwt-api-boilerplate.git nom-de-votre-projet` pour créer votre projet nommé `nom-de-votre-projet`.
- **package.json** est le fichier de configuration de votre projet. Veuillez le mettre à jour afin de :
  - donner un nom à votre projet & une description ;
  - vous identifier comme auteur.
- ⚡ Si vous avez cloné votre projet au sein d'un repo existant, Git ne traquera pas ce nouveau projet ; en effet, Git ne traque pas des projets Git dans des projets Git.
  Pour vous assurer que Git traque votre nouveau projet imbriqué dans un repo, vous devez effacer le répertoire **.git** se trouvant dans votre nouveau projet. N'hésitez pas aussi à effacer **.gitignore** se trouvant dans votre nouveau projet.
- Par contre, si vous souhaitez créer un nouveau repo à l'aide de votre boilerplate,
  vous pouvez utiliser le **.gitignore** existant. Vous pouvez aussi éventuellement utiliser le
  **.git**, mais cela signifie que vous hériterez de tous les changements associés au boilerplate,
  et que vous devrez changer l'origine (`git remote remove origin`, `git remote add origin LINK_TO_YOUR_REPO`). Nous vous recommandons plutôt d'effacer le répertoire **.git** et de
  réinitialiser un projet git (`git init`, `git remote add origin LINK_TO_YOUR_REPO`).
- Installation des dépendances et démarrage du boilerplate :

```shell
cd nom-de-votre-projet # (le nom donné au répertoire de votre projet)
npm i # (equivalent de npm install)
```

### Exécution du programme dans un environnement de développement
- Pour travailler avec un environment de développement confortable offrant un hot reload de votre application à chaque modification de script, il suffit de taper : 
```shell
npm run dev
```
- N'oubliez pas d'activer la sauvegarde automatique au sein de VS Code, car c'est à chaque sauvegarde de fichier que le hot reload va s'effectuer.

### Exécution du programme dans un environnement de production
- Pour déployer son application pour un environnement de production, il faut d'abord la "build" avec la commande :
```shell
npm run tsc
```
- Cela va générer, à partir de vos scripts `.ts`, du code JS optimisé dans le répertoire `/build` de votre application.
- Si votre build de production est réussi, vous pouvez exécuter votre application prête pour la production à l'aide de la commande :
```shell
npm run start
```


## Utilisation du linter et du formatter pour TS

- Pour bénéficier de feedback sur le code lors de son écriture, vous devez avoir installé l'extension **ESLint** au sein de VS Code.
- Vous devez aussi avoir ouvert le projet comme Workspace dans VS Code : `File`, `Open Folder...`. Le fichier de configuration de TypeScript (qui spécifie les options de compilation pour le compilateur TypeScript `tsc`) doit se trouver à la racine de votre Workspace.
- Pour formatter votre code, vous devez avoir installé l'extension **prettier** au sein de VS Code.
- Vous pouvez facilement formatter votre code :
  - soit en tapant `Alt Shift F `(`Option Shift F` sous MacOS);
  - soit en faisant un clic droit sur votre script, **Format Document** ; la première fois, il se peut que vous deviez sélectionner **prettier** comme formater : dans un fichier `.ts`, clic droit, `Format Document With...`, `Configure Default Formatter`.
- Pour info, la configuration des règles de **ESLint** se fait dans le fichier
  **.eslintrc** devant se trouver à la racine d'un projet et offert au sein du boilerplate.
- Il est possible de bénéficier d'un check du projet par le linter et de voir tous les avertissement ou erreurs en tapant cette commande dans votre projet :
```shell
npm run lint
```


## Utilisation du debugger

### Utilisation de la configuration de debug offerte
Nous vous offrons une configuration de Debug permettant de facilement déboguer plusieurs applications au sein d'un même folder de VS Code. Cette configuration se trouve dans le fichier **.vscode/launch.json**.  
Cette configuration est active au sein de VS Code que si elle se trouve à la racine du folder ouverte dans VS Code. Vous devez donc vous assurer que le dossier **.vscode** et son fichier **launch.json** se trouvent au bon endroit. Voici deux scénarios :

- Si vous ouvrez un seul projet au sein de VS Code, c'est-à-dire que le folder ouvert de VS Code est le clone de ce boilerplate) : vous ne devez pas déplacer le répertoire **.vscode**, tout est bien configuré.
- Si vous ouvrez ou folder de VS Code contenant plusieurs projets, comme par exemple un repository contenant plusieurs API : vous devez déplacer **.vscode** à la racine du folder ouvert dans VS Code.

Si vous avez plusieurs applications au sein d'un folder de VS Code, pour déboguer une application en particulier, nous vous conseillons cette approche :

- Ouvrez le fichier **package.json** de l'application à déboguer ;
- Cliquez sur l'icône **Run and Debug** à gauche de l'Explorer, puis cliquez sur **Start Debugging** (ou cliquez juste sur **F5**) en vérifiant que la configuration de debugging sélectionnée est bien nommée **Launch via NPM**.

Notons que le nom de la configuration de debugging peut facilement être modifiée en changeant la valeur de l'attribut **name** dans **/.vscode/launch.json**.

### Utilisation du debugger TS
Il existe un autre moyen de déboguer son application au sein de VS Code :
- Veuillez installer l'extension TypeScript Debugger au sein de VS Code;
- Ensuite, il vous suffit de créer une configuration de Debug (`Add Configuration...`, `TS Debug`) ou vous pouvez sélectionner la configuration offert nommée `ts-node`. Une fois que votre configuration est ouverte après avoir cliqué sur l'onglet de Debug, vous êtes prêt à déboguer.
- Ouvrez le script d'entrée de votre application : `/bin/www.ts`.
- Cliquez sur `Start Debugging` ou sur `F5` en vérifiant que la configuration de debugging sélectionnée est bien nommée `ts-node` (ou le nom que vous auriez choisi pour la configuration de votre debugger pour TS).

## Comment ajouter un package ?

- Installation d'un package : `npm i nomDuPackage`
  Pour plus d'info sur un package, ou pour trouver un package traitant d'un sujet qui vous intéresse : https://www.npmjs.com
- Modification du code pour l'utiliser, au sein de `/src/index.js` (ou tout autre module .js) : chargement de la librairie soit via `import` (ou `require`) du package. Généralement, les instructions d'installation et d'utilisation d'un package sont données sur le site de https://www.npmjs.com.
- Si quelqu'un souhaite installer et exécuter ce projet, la gestion des dépendances est très simple : copie du répertoire du projet (sans `node_modules`), `npm i`, `npm run dev`. Il n'y a donc pas de librairies à gérer manuellement pour reprendre le projet d'un tiers.

## Test des opérations offerte par l'API
- Installez l'extension **REST Client** de VS Code.
- N'oubliez pas de démarrer l'API : `npm run dev` ou utilisez votre debugger.
- N'hésitez pas à explorer les requêtes pour voir comment l'API réagit => clic sur `Send Request` au sein de `/tests/auths.http` ou `/tests/pizzas.http` par exemple.
- Si vous avez besoin de plus d'information sur comment récupérer des données suite à une requête faite via REST Client, n'hésitez pas à lire la documentation : https://github.com/Huachao/vscode-restclient

## Gestion des CORS
- La sécurité de l'API va être relâchée en gérant les Cross Origin Resource Sharing  (CORS). On va configurer le serveur de l'API en spécifiant la ou les origines pouvant lire ses ressources via un web browser (pouvant accéder à ses réponses). Cela sera fait via des « HTTP headers » ajoutés aux réponses du serveur.
- La sécurité peut être relâchée au niveau de toutes les routes en appelant le middleware **cors** (on pourrait le faire au niveau d'un router uniquement , ou d'une seule route) :  
```ts
import cors from "cors";

const corsOptions = {
  origin: [/^http:\/\/localhost/, "http://amazing.you.com"],
};

app.use(cors(corsOptions));
``` 

## Sécurisation d'opérations par JWT
- Afin de sécuriser les opérations d'écriture sur des ressources, vous pouvez appeler le middleware d’autorisation `authorize` se trouvant dans `/utils/authorize.ts`.
- Par exemple : pour protéger les opérations sur les ressources de types "pizzas" (création, suppression et modification de ressources) par `admin` seulement, dans `/routes/pizzas.ts`, les fonctions middleware `authorize` et `isAdmin` de `/utils/authorize.ts` sont utilisées ; `authorize` appelle la méthode `jwt.verify()` pour vérifier la signature et parser les infos qui sont dans le payload (`token.username`) du token.

## Hachage des passwords
- Vous pouvez hacher les passwords lors de l'enregistrement d'un utilisateur via l'appel de la méthode `hash()` de `bcrypt` au sein de `/services/users.ts `. Notons que `hash` renvoie une promesse.
- Vous pouvez comparer un password reçu en clair, lors du login, avec le password haché en utilisant la méthode compare de `bcrypt` au sein de `/services/users.ts `. Là aussi il faut gérer une promesse.

# Crédit :
- La configuration du projet pour utiliser TS & le linter a été reprise du cours de Fullstack Open (`Typing an Express app` : https://fullstackopen.com/en/part9/typing_an_express_app ainsi que via https://github.com/fullstack-hy2020/flight-diary).

# Documentation de l'API — Exercice 3.1

## Opérations disponibles

| URI | Méthode HTTP | Auths ? | Opération |
|---|---|---|---|
| **`/auth/register`** | POST | Non | REGISTER : Créer un nouvel utilisateur `{username, password}` |
| **`/auth/login`** | POST | Non | LOGIN : Authentifier un utilisateur et renvoyer un token JWT |

### 🎬 Films
| URI | Méthode HTTP | Auths ? | Opération |
|---|---|---|---|
| **`/films`** | GET | Non | READ ALL : Lire tous les films |
| **`/films/:id`** | GET | Non | READ ONE : Lire un film par ID |
| **`/films`** | POST | JWT | CREATE ONE : Créer un film `{title, director, duration, budget?, description?, imageUrl?}` |
| **`/films/:id`** | PATCH | JWT | UPDATE ONE : Modifier un film existant |
| **`/films/:id`** | DELETE | JWT | DELETE ONE : Supprimer un film existant |

### 💬 Commentaires
| URI | Méthode HTTP | Auths ? | Opération |
|---|---|---|---|
| **`/comments`** | GET | Non | READ ALL FILTERED : Lire tous les commentaires ou filtrer via `?filmId=` |
| **`/comments`** | POST | JWT | CREATE ONE : Ajouter un commentaire associé à l'utilisateur authentifié. Format `{filmId, content}` |
| **`/comments/:filmId`** | DELETE | JWT | DELETE ONE : Supprimer le commentaire du user authentifié pour un film donné |

---