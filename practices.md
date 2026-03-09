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