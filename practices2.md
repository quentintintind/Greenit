# 🔴 Problèmes critiques

## Contenu & fonctionnalités

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| Logo chargé deux fois dans le DOM | RWEB_0001 | Suppression du doublon → un seul logo rendu responsive via CSS.<br><br>```html<br><a href="#" class="nav-logo">Le Splendid</a><br>``` |
| Navigation dupliquée | RWEB_0001 | Une seule navigation + adaptation mobile via CSS.<br><br>```html<br><ul class="nav-links">...</ul><br>```<br>```css<br>@media (max-width:900px){ .nav-links{display:none;} }<br>``` |
| 11 images de drapeaux chargées | RWEB_0003 | Suppression complète → aucune ressource inutile chargée.<br><br>❌ supprimé |

---

## Images

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| Aucun format moderne | — | Suppression des images lourdes → remplacement par CSS (gradients).<br><br>```css<br>.hero-bg { background: linear-gradient(...); }<br>``` |
| Pas de width/height | RWEB_0012 | Utilisation de `aspect-ratio` pour stabiliser le layout.<br><br>```css<br>.about-img-frame { aspect-ratio: 3/4; }<br>``` |
| Pas de lazy loading | RWEB_0007 | Ajout de `loading="lazy"` sur les éléments lourds.<br><br>```html<br><iframe loading="lazy"></iframe><br>``` |

---

## Ressources tierces

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| Widget Zenchef chargé partout | RWEB_0007 | Suppression → remplacé par CTA simple (tel).<br><br>```html<br><a href="tel:0437248585" class="btn-primary">04 37 24 85 85</a><br>``` |
| Google Maps chargé immédiatement | RWEB_0007 | Lazy loading de l’iframe.<br><br>```html<br><iframe loading="lazy" ...></iframe><br>``` |
| Appel newsletter externe | RWEB_0021 | Suppression → aucune requête HTTP inutile.<br><br>❌ supprimé |

---

# 🟠 Problèmes significatifs

## HTML / DOM

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| Texte redondant | RWEB_0001 | Simplification → contenu unique.<br><br>```html<br><h1 class="hero-title">Le Splendid</h1><br>``` |
| Hiérarchie incohérente | RWEB_0012 | Structure logique h1 → h2 → h3.<br><br>```html<br><h1>...</h1><br><h2>...</h2><br><h3>...</h3><br>``` |
| Éléments cachés inutiles | RWEB_0001 | Suppression du DOM inutile.<br><br>❌ supprimé |

---

## Fichiers & formats

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| PDF menu | RWEB_0018 | Remplacé par contenu HTML léger.<br><br>```html<br><a href="#">Carte & Menus</a><br>``` |
| Pas de cache visible | — | Site statique → cache navigateur automatique.<br><br>✔️ |

---

## Scripts

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| Dépendance Zenchef | RWEB_0001 / RWEB_0012 | Site autonome (HTML/CSS/JS natif).<br><br>```html<br><script>...</script><br>``` |
| Tracking tiers | RWEB_0001 / RWEB_0003 | Aucun script externe → sobriété maximale.<br><br>❌ supprimé |

---

# 🟡 Améliorations recommandées

## UX & sobriété

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| 11 langues | RWEB_0003 / RWEB_0002 | Réduction à une langue pertinente (FR).<br><br>```html<br><html lang="fr"><br>``` |
| Formulaire chargé inutilement | RWEB_0007 | Remplacé par contact simple (tel).<br><br>```html<br><a href="tel:0437248585">...</a><br>``` |

---

## Texte & données

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| Horaires dupliqués | RWEB_0001 | Centralisation dans une seule section.<br><br>```html<br><div class="hours-table">...</div><br>``` |
| Absence de meta description | RWEB_0011 | Ajout recommandé.<br><br>```html<br><meta name="description" content="Brasserie moderne à Lyon..."><br>``` |

---

## Accessibilité / sobriété

| Problème | Pratique RWEB | Solution apportée + code |
|----------|--------------|--------------------------|
| Pas de mode sombre | RWEB_0012 | Design dark natif (OLED friendly).<br><br>```css<br>body { background:#0f0d0a; }<br>``` |
| Alt dupliqué | RWEB_0012 | Suppression des images → problème éliminé.<br><br>❌ |
| Liens nouveaux onglets | RWEB_0005 | Limité aux cas nécessaires.<br><br>`target="_blank"` uniquement si utile |

---

# ✅ Résumé des gains

Ancien site : ~5.45 Mo  
Nouveau site : ~1–1.5 Mo

Actions clés :
- Suppression des scripts tiers
- Suppression des images lourdes
- Simplification DOM
- Lazy loading
- Site statique

👉 Résultat :
- ⚡ + rapide
- 🌱 - consommation réseau
- 🔍 meilleur SEO