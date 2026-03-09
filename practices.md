🔴 Problèmes critiques
Contenu & fonctionnalités

Logo chargé deux fois dans le DOM : une instance desktop + une instance mobile dans le même HTML. Ressource dupliquée inutilement.
Navigation entièrement dupliquée dans le HTML (menu desktop + menu mobile). Le DOM contient deux fois tous les éléments de nav → surcharge HTML, rendu, et mémoire.
11 images de drapeaux (PNG) chargées pour les langues, même si l'utilisateur n'en a besoin que d'une. Aucune logique de chargement conditionnel.

Images

Aucun format moderne (WebP ou AVIF) — les images sont servies en .png depuis le CDN Zenchef.
Pas de dimensions width/height spécifiées sur les balises <img> → provoque des Layout Shifts (CLS) et empêche le navigateur de réserver l'espace avant le chargement.
Pas d'attribut loading="lazy" sur les images non critiques (logo, image de plat en bas de page).

Ressources tierces

Widget de réservation Zenchef : script tiers chargé systématiquement sur toutes les pages, même si l'utilisateur ne réserve pas.
Google Maps probablement en iframe sur la page contact : chargement immédiat d'une ressource très lourde (JS, tuiles, APIs) sans déclenchement au clic.
Appel externe newsletter (nl.zenchef.com) générant une requête HTTP supplémentaire dès le chargement de page.


🟠 Problèmes significatifs
HTML / DOM

Contenu texte redondant : "Bienvenue chez Le Splendid", puis "Le Splendid", puis "Le Splendid Brasserie LYON" apparaissent plusieurs fois dans la page pour des raisons de mise en page — à factoriser.
Hiérarchie des titres incohérente (h1 → h2 → h4 en sautant h3) → mauvaise sémantique, peut forcer des comportements de rendu inutiles.
Éléments cachés en CSS (menu mobile) présents dans le DOM mais invisibles : noeuds inutilement parsés et mis en mémoire.

Fichiers & formats

Carte & Menus en PDF : proposer un PDF directement lié depuis le menu de navigation pousse les utilisateurs à télécharger un fichier lourd. Une page HTML légère serait plus sobre.
Pas de politique de cache visible côté HTML (pas d'indication d'en-têtes Cache-Control côté meta, dépend entièrement du CDN Zenchef).

Scripts

Dépendance totale à Zenchef pour le rendu : si leur CDN est lent ou indisponible, la page est dégradée. Aucune version de secours légère.
Potentiels scripts de tracking tiers injectés via la plateforme Zenchef (analytics, pixels) non maîtrisés par le propriétaire du site.


🟡 Améliorations recommandées
UX & sobriété fonctionnelle

11 langues proposées pour un restaurant local lyonnais : est-ce vraiment utile ? Charger 11 versions et 11 drapeaux pour un usage probablement très marginal est un gaspillage de ressources.
Formulaire de contact chargé dans la page (DOM présent mais caché) même si la grande majorité des visiteurs ne l'utilise pas → à charger à la demande.

Texte & données

Répétition des horaires : les horaires apparaissent dans la page principale et probablement aussi sur la page contact/accès → duplication de données à centraliser.
Absence de meta description (non visible dans le source récupéré) → peut forcer les moteurs à générer des extraits plus lourds.

Accessibilité / sobriété

Pas d'adaptation au mode sombre (prefers-color-scheme) → sur mobile, un fond blanc consomme plus d'énergie sur les écrans OLED que des tons sombres.
Pas d'attribut alt optimisé sur le logo (alt = "Logo Le Splendid" répété deux fois, ce qui confirme le doublon).
Liens "ouvre une nouvelle fenêtre" systématiques : ouvrir de nouveaux onglets multiplie les instances de rendu navigateur sans nécessité réelle.


Résumé des priorités
PrioritéAction🔴Supprimer la duplication du logo et de la nav dans le DOM🔴Passer les images en WebP + ajouter lazy loading + dimensions🔴Charger le widget de réservation et la carte Maps au clic uniquement🟠Supprimer ou conditionner le chargement des 11 drapeaux🟠Remplacer le PDF menu par une page HTML légère🟠Nettoyer les éléments DOM cachés (menu mobile, formulaire contact)🟡Questionner la pertinence des 11 langues🟡Ajouter le support prefers-color-scheme



a associer le site web initial avait donbc ces problemes : D'après les résultats de votre audit, votre page pèse 5,45 Mo, soit plus du double de la médiane du web (2,41 Mo). C'est un "poids lourd" qui pénalise votre score RSE (consommation de bande passante) et votre SEO (vitesse de chargement).

Voici un plan d'action technique pour diviser ce poids par trois :
1. Cure de minceur pour les Images (Le levier n°1)

C'est généralement 80% du poids d'un site d'hôtel.

    Passez au WebP ou AVIF : Remplacez vos formats .jpg ou .png. Le WebP offre une compression jusqu'à 30% supérieure à qualité égale.

    Redimensionnement "Responsive" : Ne chargez pas une image de 4000px de large si elle s'affiche dans un bloc de 400px sur mobile. Utilisez l'attribut srcset en HTML pour servir la bonne taille selon l'écran.

    Compression sans perte : Utilisez des outils comme TinyPNG ou Squoosh avant d'uploader vos visuels.

2. Nettoyage du Code (HTML, CSS, JS)

Le site actuel semble charger beaucoup de bibliothèques externes.

    Minification : Supprimez tous les espaces, commentaires et sauts de ligne inutiles dans vos fichiers .css et .js.

    Suppression du "Dead Code" : Les thèmes d'hôtels pré-construits chargent souvent des fonctions (calendriers, galeries, polices) que vous n'utilisez pas. Désactivez ce qui est superflu.

    Chargement différé (Lazy Loading) : Paramétrez votre site pour que les images en bas de page ne se chargent que lorsque l'utilisateur descend (scroll).

3. Remplacer le visuel par du structurel

    Pictos en SVG ou Icon Fonts : Au lieu d'utiliser des images .png pour vos icônes (Wifi, Petit-déjeuner, Parking), utilisez du format SVG. C'est du code pur, ultra-léger et vectoriel (toujours net).

    Effets CSS : Utilisez le code CSS pour vos dégradés, arrondis de boutons ou ombres portées au lieu de charger des images décoratives.

4. Optimisation de la Mise en cache

C'est le critère cité dans votre audit ("Facilitez la mise en cache").

    Principe : Indiquez au navigateur du visiteur de conserver les éléments du site (logo, menu, CSS) en mémoire locale.

    Bénéfice : Lors de la deuxième visite, le navigateur ne retélécharge rien. La page s'affiche instantanément.

Comparatif : Avant vs Après Optimisation
Élément	État Actuel (Estimation)	Cible Optimisée
Images	4.5 Mo (HD non compressé)	0.8 Mo (WebP progressif)
Scripts JS	0.6 Mo (Scripts tiers inutiles)	0.2 Mo (Minifiés)
Polices (Fonts)	300 Ko (Toutes les graisses)	50 Ko (Woff2 uniquement)
Poids Total	~5.5 Mo	< 1.5 Mo

Souhaitez-vous que je regarde une page spécifique du site (comme la galerie photos) pour vous dire exactement quelles images bloquent le score ?
