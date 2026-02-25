# CLAUDE.md — Projet ELEVIA-SITE

## Règles de travail

- **Toujours parler en français**
- **Montrer les changements avant de les appliquer** — ne jamais modifier sans validation
- **Ne jamais supprimer de contenu sans demander** — toujours confirmer avant suppression
- **Garder le style visuel cohérent entre toutes les pages** — respecter la palette, les fonts, les espacements et le ton

---

## Qu'est-ce qu'Élevia ?

Élevia est un **service de nutrition personnalisée** créé par **Audric Didderen**, diététicien diplômé basé en Belgique (INAMI 478749). Le site est hébergé sur **elevia.be**.

Le concept : chaque client reçoit un **plan nutritionnel sur mesure** basé sur un questionnaire approfondi (60+ questions), livré en 72h. Le plan utilise un **système d'équivalences alimentaires** qui offre structure et flexibilité. Une **application compagnon "Cockpit"** permet le suivi quotidien (repas, progrès, recettes personnalisées, feedback intelligent).

**3 formules :**
- Plan seul — 89€
- Plan + Cockpit 6 mois — 169€ (recommandé)
- Plan + Cockpit 12 mois — 229€

Le positionnement est **premium accessible** : identité visuelle soignée (navy/or/crème), approche professionnelle mais ton direct (tutoiement).

---

## Structure du projet

```
ELEVIA-SITE/
├── .claude/                    # Dossier Claude Code
├── .git/                       # Dépôt Git
├── .gitignore                  # Fichiers ignorés
├── CLAUDE.md                   # Ce fichier
│
├── index.html                  # Page d'accueil (landing page principale)
├── systeme.html                # Présentation du système Élevia en 3 couches
├── offre.html                  # Tarifs et détails des offres
├── cockpit.html                # Showcase de l'application Cockpit
├── apropos.html                # Page À propos (présentation d'Audric)
├── articles.html               # Article de blog (un seul pour l'instant)
├── contact.html                # Formulaire de contact (via Formspree)
├── merci.html                  # Page post-paiement (noindex)
├── 404.html                    # Page d'erreur 404
├── confidentialite.html        # Politique de confidentialité RGPD
├── mentions-legales.html       # Mentions légales
├── cookie-banner-snippet.html  # Snippet réutilisable du cookie banner
│
├── favicon.svg                 # Favicon SVG (É doré sur fond navy)
├── favicon-32x32.png           # Favicon PNG 32x32
├── apple-touch-icon.png        # Icône Apple Touch 180x180
├── og-image.svg                # Image Open Graph (source SVG)
└── og-image.jpg                # Image Open Graph (1200x630, pour partage social)
```

### Dossier `images/` (référencé mais non vérifié)

Les pages référencent des images qui doivent exister :
- `images/audric-portrait.webp` — Portrait (apropos.html)
- `images/audric-cuisine.webp` — Photo cuisine (apropos.html)
- `images/articles/calories-hero.webp` — Hero article (articles.html)
- `images/articles/placeholder-*.webp` — Articles suggérés (articles.html)
- `images/mockups/cockpit-*.webp` — 5 screenshots app (cockpit.html)

---

## Pages et leur contenu

| Page | Description | Sections clés |
|------|-------------|---------------|
| `index.html` | Landing page principale | Hero, mots-scroll (Structure/Liberté/Résultats), constat, méthode (4 cartes), preuves, app Cockpit, livrables, pricing teaser, CTA |
| `systeme.html` | Le système Élevia | Confusion vs Clarté, 3 couches (plan, app, cadre), comparatif premium, devise |
| `offre.html` | Tarifs détaillés | Ancrage prix, 3 cartes pricing, early access, processus 4 étapes, FAQ |
| `cockpit.html` | Application Cockpit | Pain points, solutions, showcase sticky-scroll avec mockup iPhone (5 étapes) |
| `apropos.html` | À propos d'Audric | Portrait, origin story, vision, credentials (4 cartes) |
| `articles.html` | Blog — article unique | "Pourquoi les calories ne suffisent pas", TOC sidebar, share bar, FAQ, sources |
| `contact.html` | Contact | Formulaire (Formspree), infos contact, FAQ |
| `merci.html` | Post-paiement | Carte de confirmation, 3 étapes suivantes |
| `404.html` | Erreur 404 | Logo fantôme, message, retour accueil |
| `confidentialite.html` | RGPD | Données collectées, base légale, droits |
| `mentions-legales.html` | Légal | Éditeur, hébergeur, propriété intellectuelle |

---

## Couleurs (variables CSS)

```css
/* Couleurs principales */
--navy: #0E1E2E;          /* Fond principal sombre */
--navy-deep: #091520;     /* Footer, fonds très sombres */
--navy-light: #152A3D;    /* Variante navy claire */

--gold: #C6A05B;          /* Accent principal (CTAs, titres em, icônes) */
--gold-light: #D4B878;    /* Hover doré */
--gold-pale: #E8D5A8;     /* Bordures hover */
--gold-glow: rgba(198, 160, 91, 0.15);  /* Halos radiaux */

--cream: #F6F3EE;         /* Fond clair principal */
--cream-dark: #EDE8E0;    /* Variante crème foncée */
--white: #FFFFFF;          /* Cartes, éléments blancs */

/* Texte */
--text-dark: #1A1A1A;     /* Texte principal sur fond clair */
--text-muted: #6B7280;    /* Texte secondaire sur fond clair */
--text-soft: #8B9AAC;     /* Texte secondaire sur fond sombre */

/* Bordures */
--border-soft: #F5EEE1;   /* Bordures subtiles sur fond clair */
```

---

## Typographie

```css
--serif: 'Cormorant Garamond', Georgia, serif;   /* Titres, headlines, citations */
--sans: 'Outfit', -apple-system, sans-serif;      /* Corps, labels, boutons */
```

Chargées via **Google Fonts** :
- Cormorant Garamond : poids 300, 400, 500, 600, 700 + italiques
- Outfit : poids 200, 300, 400, 500, 600

---

## Stack technique

- **HTML/CSS/JS vanilla** — zéro framework, zéro librairie
- **Pas de fichier CSS/JS externe** — tout est inline dans chaque page
- **Google Fonts** — seule dépendance externe (CDN)
- **Formspree** — backend formulaire de contact (`https://formspree.io/f/xqakrgqp`)
- **Hostinger** — hébergeur
- **Pas de build system** — pas de bundler, pas de préprocesseur

### Patterns JS récurrents
- `IntersectionObserver` avec `data-reveal` pour les animations d'apparition au scroll
- Barre de progression de lecture (`scroll-progress`)
- Header qui change au scroll (classe `scrolled`)
- Hamburger mobile avec menu plein écran
- FAQ en accordéon (sur plusieurs pages)
- Grain overlay SVG en `position: fixed`
- `prefers-reduced-motion` respecté sur toutes les pages

---

## Problèmes connus / À corriger

### Critique
1. **Lien "À propos" cassé sur 7 pages** — `systeme.html`, `offre.html`, `cockpit.html`, `articles.html`, `contact.html`, `confidentialite.html`, `mentions-legales.html` pointent vers `/a-propos.html` alors que le fichier est `apropos.html` (sans tiret)
2. **Incohérence des domaines** — `elevia.be` (index), `elevia-nutrition.fr` (articles), `elevia-nutrition.com` (confidentialité) sont mélangés dans les meta/canonical
3. **Placeholders non remplis** dans les pages légales (adresse, statut juridique, n° BCE, ville du tribunal)

### Important
4. **Cookie banner absent** sur 7 pages (index, systeme, offre, cockpit, apropos, articles, contact) — présent uniquement dans mentions-legales et confidentialite
5. **Meta OG / Twitter Cards absentes** sur la plupart des pages (seulement index et articles les ont)
6. **Favicon non référencé** dans les pages autres que index.html
7. **Code CSS/JS dupliqué massivement** entre les pages — toute modification doit être répliquée sur 10+ fichiers
8. **Google Analytics non configuré** — `loadAnalytics()` commenté, ID = placeholder `TON_ID_GA`

### Souhaitable
9. **Pas de page listing d'articles** — le breadcrumb référence `/articles` mais cette page n'existe pas
10. **Images non vérifiées** — portraits, mockups, images articles peuvent manquer
11. **Header/footer pas toujours cohérents** entre les pages (Contact absent du header sur certaines pages, À propos/Cockpit absents du footer)
