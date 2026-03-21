# 🔴 Problèmes critiques

## Contenu & fonctionnalités

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| Logo chargé deux fois dans le DOM | RWEB_0001 — Supprimer tout élément inutile pour alléger le site | Suppression du doublon → un seul logo responsive.<br><br>```html<br><a href="#" class="nav-logo">Le Splendid</a><br>``` |
| Navigation dupliquée | RWEB_0001 — Éviter les duplications inutiles dans le DOM | Une seule navigation + responsive en CSS.<br><br>```html<br><ul class="nav-links">...</ul><br>```<br>```css<br>@media (max-width:900px){ .nav-links{display:none;} }<br>``` |
| 11 drapeaux chargés | RWEB_0003 — Supprimer les fonctionnalités non utilisées | Suppression complète des langues inutiles.<br><br>❌ supprimé |

---

## Images

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| Aucun format optimisé | Optimisation image — Réduire le poids des médias | Suppression des images → remplacées par CSS.<br><br>```css<br>.hero-bg { background: linear-gradient(...); }<br>``` |
| Pas de width/height | RWEB_0012 — Design simple et stable (éviter les décalages) | Utilisation de `aspect-ratio`.<br><br>```css<br>.about-img-frame { aspect-ratio: 3/4; }<br>``` |
| Pas de lazy loading | RWEB_0007 — Charger les éléments uniquement quand nécessaire | Ajout de `loading="lazy"`.<br><br>```html<br><iframe loading="lazy"></iframe><br>``` |

---

## Ressources tierces

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| Widget Zenchef chargé partout | RWEB_0007 — Charger à la demande | Suppression → bouton simple.<br><br>```html<br><a href="tel:0437248585" class="btn-primary">04 37 24 85 85</a><br>``` |
| Google Maps lourd | RWEB_0007 — Éviter les chargements inutiles | Lazy loading de la carte.<br><br>```html<br><iframe loading="lazy"></iframe><br>``` |
| Newsletter externe | RWEB_0021 — Limiter les appels HTTP | Suppression → aucune requête inutile.<br><br>❌ supprimé |

---

# 🟠 Problèmes significatifs

## HTML / DOM

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| Texte redondant | RWEB_0001 — Supprimer les contenus dupliqués | Simplification du contenu.<br><br>```html<br><h1 class="hero-title">Le Splendid</h1><br>``` |
| Hiérarchie incohérente | RWEB_0012 — Structurer correctement le contenu | Hiérarchie logique.<br><br>```html<br><h1>...</h1><br><h2>...</h2><br><h3>...</h3><br>``` |
| Éléments cachés inutiles | RWEB_0001 — Éviter les éléments non visibles inutiles | Suppression du DOM inutile.<br><br>❌ supprimé |

---

## Fichiers & formats

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| PDF menu | RWEB_0018 — Favoriser des pages HTML légères | Remplacement par HTML.<br><br>```html<br><a href="#">Carte & Menus</a><br>``` |
| Pas de cache | Optimisation — Réduire les rechargements | Site statique → cache navigateur.<br><br>✔️ |

---

## Scripts

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| Dépendance Zenchef | RWEB_0001 — Réduire les dépendances inutiles | Site autonome (HTML/CSS/JS).<br><br>```html<br><script>...</script><br>``` |
| Tracking tiers | RWEB_0003 — Supprimer les scripts inutiles | Aucun script externe.<br><br>❌ supprimé |

---

# 🟡 Améliorations recommandées

## UX & sobriété

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| 11 langues | RWEB_0002 — Adapter le site au besoin réel | Une seule langue pertinente.<br><br>```html<br><html lang="fr"><br>``` |
| Formulaire inutile | RWEB_0007 — Charger seulement si nécessaire | Remplacé par téléphone.<br><br>```html<br><a href="tel:0437248585">...</a><br>``` |

---

## Texte & données

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| Horaires dupliqués | RWEB_0001 — Centraliser les données | Une seule section.<br><br>```html<br><div class="hours-table">...</div><br>``` |
| Pas de meta description | RWEB_0011 — Améliorer SEO et pertinence | Ajout meta.<br><br>```html<br><meta name="description" content="Brasserie moderne à Lyon..."><br>``` |

---

## Accessibilité / sobriété

| Problème | Pratique RWEB (explication) | Solution apportée + code |
|----------|-----------------------------|--------------------------|
| Pas de mode sombre | RWEB_0012 — Design adapté aux usages | Design dark natif.<br><br>```css<br>body { background:#0f0d0a; }<br>``` |
| Alt dupliqué | RWEB_0012 — Améliorer accessibilité | Images supprimées → problème éliminé |
| Nouveaux onglets | RWEB_0005 — Optimiser le parcours utilisateur | Usage limité de `target="_blank"` |

---

# ✅ Résumé

Ancien site : ~5.45 Mo  
Nouveau site : ~1–1.5 Mo  

✔ Suppression scripts tiers  
✔ Suppression images lourdes  
✔ DOM simplifié  
✔ Lazy loading  
✔ Site statique  

👉 Résultat :
- ⚡ plus rapide  
- 🌱 moins énergivore  
- 🔍 meilleur SEO  