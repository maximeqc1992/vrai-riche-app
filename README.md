# Vrai Riche — Badge (projet Capacitor)

Ce dossier contient un projet Capacitor minimal qui emballe ta page `www/index.html`
(le badge) dans une vraie app iOS. Comme tu n'as pas de Mac, tout se compile et se
soumet dans le cloud via Codemagic — tu n'as jamais besoin d'ouvrir Xcode.

## Ce qu'il y a dans ce dossier

- `www/index.html` — ton badge, tel quel (c'est le contenu de l'app)
- `package.json` — dépendances Capacitor
- `capacitor.config.json` — configuration de l'app (nom, identifiant)
- `codemagic.yaml` — config de compilation/soumission automatique dans le cloud

## Étapes à suivre

### 1. Mets ce dossier sur GitHub
Crée un dépôt (public ou privé, peu importe) sur github.com et pousse ce dossier
dedans. Codemagic se connecte directement à un dépôt Git.

### 2. Choisis ton identifiant d'app (bundle ID)
Dans `capacitor.config.json` et `codemagic.yaml`, remplace
`com.maxime.vrairiche` par ton propre identifiant inversé, unique
(ex: `com.tonnom.vrairiche`). C'est cet identifiant que tu utiliseras
aussi dans App Store Connect.

### 3. Inscris-toi au Apple Developer Program
Sur developer.apple.com — 99 $ US/an, depuis n'importe quel navigateur.

### 4. Crée la fiche de l'app sur App Store Connect
Sur appstoreconnect.apple.com : nouvelle app, même bundle ID qu'à l'étape 2,
nom, catégorie, prix, captures d'écran, politique de confidentialité (un lien
vers une simple page web suffit).

### 5. Crée un compte Codemagic et connecte ton dépôt
Sur codemagic.io (plan gratuit suffisant pour commencer). Codemagic détecte
automatiquement le fichier `codemagic.yaml`.

### 6. Connecte Codemagic à App Store Connect
Dans Codemagic : Teams → Integrations → App Store Connect. Tu génères une clé
API depuis App Store Connect (Users and Access → Keys) et tu la colles dans
Codemagic. C'est ce qui permet à Codemagic de signer et soumettre l'app sans
Mac ni Xcode de ton côté.

### 7. Lance le build
Dans Codemagic, démarre le workflow `ios-vrai-riche`. Il va :
compiler l'app → la signer → l'envoyer sur TestFlight automatiquement.

### 8. Teste sur TestFlight, puis soumets pour révision
Une fois satisfait du résultat sur TestFlight (installable sur ton iPhone via
l'app TestFlight), passe le statut de la version sur "Ready for Sale" dans
App Store Connect et soumets pour révision Apple.

## À savoir
Une app à un seul écran est parfois refusée par Apple pour "manque de
contenu suffisant" (règle 4.2 des App Store Review Guidelines). Si ça arrive,
le plus simple est d'ajouter un peu plus de substance : plusieurs styles de
badge, un historique des badges créés, une page "à propos", etc.
