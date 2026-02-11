# CLAUDE.md - Taigaschool Investment One-Pager

> **Documentatie voor AI Agents (Claude Code)**  
> **Project:** Taigaschool Eco Hotel Investment Website  
> **Versie:** 1.0.0  
> **Laatst bijgewerkt:** 9 februari 2026  
> **Doel:** Professionele investeringspresentatie voor Newsec Finland & OP Bank

---

## 📋 SNELLE START (Quick Start)

```bash
# Lokale ontwikkeling
npx serve .

# Of open direct in browser
open index.html

# Deploy naar Vercel
vercel --prod
```

**Belangrijke URLs:**
- Live site: https://taigaschool-investment.vercel.app
- GitHub: [TOEVOEGEN NA PUSH]

---

## 🎯 PROJECTOVERZICHT

### Wat is dit project?

Een **statische, single-page website** die dient als professionele investeringspresentatie voor het Taigaschool Eco Hotel in Finland. De site is ontworpen voor:

1. **Newsec Finland Oy** - AKA-gecertificeerde vastgoedwaardering
2. **OP Financial Group** - Financieringsbeoordeling
3. **Potentiële investeerders** - Samenvatting van de investeringskans

### Unieke verkoopargumenten (USPs) van het vastgoed:

| Kenmerk | Waarde |
|---------|--------|
| **NATO NCAGE** | Enige private hospitality in Finland met NAVO-certificering |
| **Green Key 5-Star** | Hoogste ecologische certificering |
| **Ultra-lean OpEx** | 49.9% vs 65-75% industriegemiddelde |
| **Multi-stream** | 6 gediversifieerde inkomstenstromen |
| **Zero mortgage** | 100% eigendom, maximale financieringsflexibiliteit |

---

## 🏗️ ARCHITECTUUR

### Tech Stack

```
┌─────────────────────────────────────────┐
│           PRESENTATIELAAG               │
│  ┌─────────────────────────────────┐    │
│  │  HTML5 (Single Page)            │    │
│  │  ├─ Semantische structuur       │    │
│  │  ├─ Accessibility (ARIA)        │    │
│  │  └─ SEO meta tags               │    │
│  └─────────────────────────────────┘    │
│  ┌─────────────────────────────────┐    │
│  │  CSS3 (Custom, Geen Framework)  │    │
│  │  ├─ CSS Variables (theming)     │    │
│  │  ├─ Flexbox & Grid layouts      │    │
│  │  ├─ Responsive breakpoints      │    │
│  │  └─ Animaties & transitions     │    │
│  └─────────────────────────────────┘    │
│  ┌─────────────────────────────────┐    │
│  │  Vanilla JavaScript (ES6+)      │    │
│  │  ├─ Language toggle systeem     │    │
│  │  ├─ Scroll animations           │    │
│  │  ├─ Intersection Observer API   │    │
│  │  └─ Event delegation            │    │
│  └─────────────────────────────────┘    │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│           HOSTING (Vercel)              │
│  ├─ Static deployment                   │
│  ├─ Global CDN                          │
│  ├─ HTTPS/SSL                           │
│  └─ Custom domain support               │
└─────────────────────────────────────────┘
```

### Bestandsstructuur

```
taigaschool-onepager/
│
├── 📄 index.html          # Hoofdbestand (46KB) - Complete SPA
├── ⚙️ vercel.json         # Vercel deployment configuratie
├── 📓 CLAUDE.md           # Dit document - AI context
├── 📖 README.md           # Publieke documentatie
├── 🚫 .gitignore          # Git uitsluitingen
└── 🗂️ .vercel/            # Vercel CLI cache (gitignored)
```

**Belangrijk:** Dit is een **zero-dependency** project. Geen npm packages, geen build step, geen frameworks.

---

## 🎨 DESIGN SYSTEEM

### Kleurenpalet (CSS Variables)

```css
:root {
  --primary:       #1a3a2a;  /* Donkergroen - Hoofdkleur */
  --primary-light: #2d5a45;  /* Midden groen */
  --accent:        #c9a227;  /* Goud - Accenten/CTA */
  --accent-light:  #e0b83a;  /* Licht goud */
  --dark:          #0d1f16;  /* Heel donker */
  --light:         #f8f9f7;  /* Off-white achtergrond */
  --text:          #2c3e2d;  /* Body tekst */
  --text-light:    #5a6b5c;  /* Secundaire tekst */
  --white:         #ffffff;  /* Puur wit */
}
```

### Typografie

| Element | Font | Gewicht | Grootte |
|---------|------|---------|---------|
| Hero H1 | Playfair Display | 600 | clamp(2.5rem, 6vw, 5rem) |
| Section H2 | Playfair Display | 400-700 | clamp(2rem, 4vw, 3rem) |
| Body | Inter | 300-700 | 1rem (16px) |
| Labels | Inter | 600 | 0.8-0.9rem |
| Stats | Inter | 700 | 2.5-3rem |

### Layout Grid

- **Max-width:** 1200px (container)
- **Padding:** 40px (desktop), 20px (mobile)
- **Grid:** CSS Grid + Flexbox combinatie
- **Breakpoints:**
  - Desktop: > 1024px
  - Tablet: 768px - 1024px  
  - Mobile: < 768px

### Componenten Bibliotheek

#### 1. Cards
```
┌─────────────────────────┐
│  ┌─────┐                │
│  │ ICO │  Titel         │
│  │ N   │                │
│  └─────┘  Beschrijving  │
│           tekst hier... │
└─────────────────────────┘

Classes: .card
Hover: translateY(-5px) + shadow vergroting
```

#### 2. Metric Cards (Donkere achtergrond)
```
┌─────────────────────────┐
│                         │
│       €2.87M            │ ← .metric-number (goud)
│    Current Value        │ ← .metric-label
│    (Stabilized 2028)    │ ← .metric-sublabel
│                         │
└─────────────────────────┘

Classes: .metric-card
Background: rgba(255,255,255,0.05) + backdrop-filter
```

#### 3. Revenue Bars
```
Leadership Retreats    45.5%
████████████████████░░░░░

Classes: .revenue-item > .revenue-bar-fill
Animation: width transition op scroll
```

#### 4. Language Toggle
```
┌──────┬──────┐
│  EN  │  FI  │  ← fixed position top-right
│active│      │
└──────┴──────┘

Classes: .lang-toggle > .lang-btn
Active: background var(--primary)
```

---

## 🔧 FUNCTIONALITEIT

### 1. Taalwissel Systeem (Bilingual)

**Mechanisme:**
```javascript
// Data-attribuut selector systeem
[data-lang="en"]      // Engelse content
[data-lang="fi"]      // Finse content
[data-lang].active    // Zichtbare content

// Toggle werking:
1. Klik op taal-knop
2. Verwijder .active van alle [data-lang]
3. Voeg .active toe aan gekozen taal
4. Update HTML lang attribuut
```

**Implementatie:**
- Alle tekstuele elementen hebben DUBBELE nodes (EN + FI)
- CSS togglet zichtbaarheid met `.active` class
- Geen page reload nodig
- Instant language switch

**Voorbeeld:**
```html
<h2 data-lang="en" class="active">Investment Opportunity</h2>
<h2 data-lang="fi">Sijoitusmahdollisuus</h2>
```

### 2. Scroll Animaties

**Gebruikte APIs:**
```javascript
// Intersection Observer voor scroll-triggering
const observer = new IntersectionObserver(callback, {
  threshold: 0.1,
  rootMargin: '0px 0px -50px 0px'
});

// Animatie keyframes
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0); }
}
```

**Getriggerde elementen:**
- Cards (staggered fade-in)
- Metric cards
- Certificatie badges
- Revenue bars (width animatie)

### 3. Navigation Scroll Effect

```javascript
// Bij scroll > 100px:
.nav.scrolled {
  background: rgba(255,255,255,0.95);
  backdrop-filter: blur(10px);
  box-shadow: var(--shadow);
}
```

### 4. Responsive Gedrag

**Mobile (< 768px):**
- Hero stats: 2-koloms grid
- Navigation: kleinere padding
- Language toggle: dichter bij rand
- Font sizes: aangepast via clamp()
- Tables: horizontaal scrollbaar indien nodig

---

## 📊 INHOUDSSTRUCTUUR

### Section Flow

```
1. HERO
   ├── NATO Badge
   ├── Hoofdtitel (EN/FI)
   ├── Subtitel
   └── Stats (4 metrics)

2. STRATEGIC ASSETS
   ├── 4 Feature Cards:
   │   ├── NATO NCAGE Certified
   │   ├── Green Key 5-Star
   │   ├── Ultra-Lean Operations
   │   └── Lake Kitka Location

3. METRICS (Donkere achtergrond)
   ├── €487K Gross Revenue
   ├── 65% Institutional Revenue
   ├── 7 Hotel Units
   └── 10 Camper Pitches

4. REVENUE STREAMS
   ├── Progress bars (5 streams):
   │   ├── Leadership Retreats (45.5%)
   │   ├── Boutique Hotel (24.2%)
   │   ├── NATO Training (19.7%)
   │   ├── Luxury Camper (6.2%)
   │   └── Lakeside Cabin (4.3%)

5. VALUATION TABLE
   ├── Direct Capitalization (Y1 & Y3)
   ├── 10-Year DCF
   ├── Market Comparison
   └── Recommended Range Box

6. FINANCING
   ├── 3 Cards:
   │   ├── 60% LTV Recommended
   │   ├── Strong DSCR Profile
   │   └── Zero Current Debt

7. CERTIFICATIONS
   ├── NATO NCAGE Badge
   ├── Green Key 5-Star Badge
   ├── Booking.com 9.2/10 Badge
   └── Visit Finland Badge

8. CTA SECTION
   ├── Headline
   ├── Description
   └── Contact Button

9. FOOTER
   └── Legal info & Reference
```

---

## 💰 FINANCIËLE DATA (Referentie)

### Kerngetallen (hardcoded in HTML)

| Metric | Waarde | Locatie in HTML |
|--------|--------|-----------------|
| **Year 1 Value** | €2,870,000 | Hero stats + Valuation table |
| **Year 3 Stabilized** | €5,687,000 | Hero stats + Valuation table |
| **NOI Margin Y1** | 50.1% | Section metrics |
| **DSCR Y1** | 1.77× | Financing section |
| **Gross Revenue Y1** | €487,480 | Metrics section |
| **OpEx Ratio** | 49.9% | Strategic assets card |
| **LTV** | 60% (€1,722,000) | Financing card |
| **Interest Rate** | 5.0% | Financing card |

### Waarderingsmethodologie

```
DIRECTE KAPITALISATIE (Primary method)
├── Year 1: €243,980 NOI ÷ 8.5% = €2,870,000
├── Year 3: €454,914 NOI ÷ 8.0% = €5,687,000
└── Aanbevolen range: €2.8M - €3.5M

10-YEAR DCF (Cross-check)
├── Discount rate: 9.5%
├── Terminal cap: 7.5%
└── Value: €5,917,000

MARKTVERGELIJKING
├── €300K/unit × 8 units
├── Camper park premium
├── NATO certificering premium (+15-25%)
└── Range: €2.6M - €3.5M
```

---

## 🚀 DEPLOYMENT

### Vercel Configuratie (vercel.json)

```json
{
  "version": 2,
  "builds": [
    {
      "src": "index.html",
      "use": "@vercel/static"
    }
  ],
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ],
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=3600"
        }
      ]
    }
  ]
}
```

### Deploy Stappen

```bash
# 1. Install Vercel CLI
npm i -g vercel

# 2. Login (eenmalig)
vercel login

# 3. Deploy (development)
vercel

# 4. Deploy (production)
vercel --prod
```

### Environment Variabelen

**Geen environment variabelen nodig** - dit is een 100% static site.

---

## 📝 CONTENT GUIDELINES

### Tekstuele Aanpassingen

**Om tekst te wijzigen:**

1. Zoek het element met `data-lang="en"` of `data-lang="fi"`
2. Wijzig de content
3. **Belangrijk:** Update BEIDE talen consistent

**Voorbeeld:**
```html
<!-- OUD -->
<p data-lang="en" class="active">Gross Revenue Y1</p>
<p data-lang="fi">Bruttotulo V1</p>

<!-- NIEUW -->
<p data-lang="en" class="active">Total Income Year 1</p>
<p data-lang="fi">Kokonaistulo Vuosi 1</p>
```

### Financiële Updates

Bij het wijzigen van financiële cijfers:

1. **Update ALLE voorkomende plaatsen:**
   - Hero stats sectie
   - Metrics sectie
   - Valuation table
   - Financing cards

2. **Controleer consistentie:**
   ```bash
   # Zoek alle euro bedragen
   grep -n "€[0-9]" index.html
   ```

3. **Percentage berekeningen:**
   - OpEx ratio = OpEx / Revenue
   - NOI Margin = NOI / Revenue
   - DSCR = NOI / Debt Service

---

## 🐛 DEBUGGING

### Veelvoorkomende Issues

#### 1. Language toggle werkt niet
```javascript
// Check in console:
document.querySelectorAll('[data-lang]').length
// Moet > 0 zijn

// Check of .active correct wordt gezet:
document.querySelectorAll('[data-lang="en"]').forEach(el => console.log(el.classList.contains('active')))
```

#### 2. Animaties werken niet
```javascript
// Controleer IntersectionObserver support:
'IntersectionObserver' in window  // true?

// Forceer animatie voor test:
document.querySelectorAll('.card').forEach(el => {
  el.classList.add('animate-in');
});
```

#### 3. Responsive layout breekt
```css
/* Test breakpoints in DevTools */
/* Mobile: 375px, 768px */
/* Tablet: 1024px */
/* Desktop: 1440px */
```

### Browser Support

| Browser | Versie | Status |
|---------|--------|--------|
| Chrome | 80+ | ✅ Full |
| Firefox | 75+ | ✅ Full |
| Safari | 13+ | ✅ Full |
| Edge | 80+ | ✅ Full |
| IE11 | - | ❌ Niet ondersteund |

---

## 🔒 SECURITY & PRIVACY

### Huidige status:
- ✅ Geen tracking scripts
- ✅ Geen cookies
- ✅ Geen external requests (behalve Google Fonts)
- ✅ Geen form submissions
- ✅ HTTPS enforced (Vercel)

### Contact button:
```html
<!-- Mailto link - geen server-side processing -->
<a href="mailto:info@rinkgroup.fi">Contact</a>
```

---

## 🔄 CI/CD WORKFLOW

### Git Workflow

```bash
# Feature development
git checkout -b feature/naam
# ... wijzigingen ...
git add .
git commit -m "Beschrijving"
git push origin feature/naam

# Merge naar main
git checkout main
git merge feature/naam
git push origin main

# Auto-deploy naar Vercel
# (gekoppeld aan GitHub webhook)
```

### Pre-deploy Checklist

- [ ] Alle teksten in BEIDE talen gecontroleerd
- [ ] Financiële cijfers gevalideerd
- [ ] Responsive test op mobiel
- [ ] Language toggle getest
- [ ] Links werken (mailto, etc.)
- [ ] Console geen errors

---

## 📚 BRONNEN & REFERENTIES

### Documentatie
- [Vercel Static Deploy](https://vercel.com/docs/concepts/deployments/overview)
- [Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)
- [CSS Clamp()](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp)

### Investeringsdocument
- Origineel document: `C:\Users\info\taigaschool-onepager.html` (oorspronkelijk)
- Volledig verslag: Zie gebruikersdirectory voor TES-NEWSEC-2026-Q1.md

### Contact
- **Eigenaar:** Marco Rink / Rink Group Oy
- **Doel:** Newsec Finland Oy & OP Financial Group
- **Datum:** 8 februari 2026

---

## 🎓 VOOR CLAUDE CODE AGENTS

### Context voor edits

Wanneer je wijzigingen aanbrengt:

1. **Altijd beide talen updaten** - Consistentie is cruciaal
2. **Behoud design systeem** - Gebruik CSS variables
3. **Test responsive** - Mobile-first mentaliteit
4. **Geen externe dependencies** - Keep it zero-dependency
5. **Documenteer in CHANGELOG** - Bij significante wijzigingen

### Snelle commands

```bash
# Zoek alle tekst in EN
findstr /s /i "data-lang=\"en\"" index.html

# Tel aantal sections
grep -c "<section" index.html

# Validatie HTML
npx html-validate index.html
```

### Extend scenario's

**Nieuwe sectie toevoegen:**
```html
<section class="section">
  <div class="section-header">
    <span class="section-tag" data-lang="en" class="active">Tag EN</span>
    <span class="section-tag" data-lang="fi">Tag FI</span>
    <h2 data-lang="en" class="active">Title EN</h2>
    <h2 data-lang="fi">Title FI</h2>
  </div>
  <!-- Content -->
</section>
```

**Nieuwe card toevoegen:**
```html
<div class="card">
  <div class="card-icon">
    <svg>...</svg>
  </div>
  <h3 data-lang="en" class="active">Title EN</h3>
  <h3 data-lang="fi">Title FI</h3>
  <p data-lang="en" class="active">Desc EN</p>
  <p data-lang="fi">Desc FI</p>
</div>
```

---

## ✅ CHECKLIST: Project Compleetheid

| Aspect | Status | Notes |
|--------|--------|-------|
| HTML structuur | ✅ | Semantisch correct |
| CSS styling | ✅ | Custom, responsive |
| JS functionaliteit | ✅ | Lang toggle, animaties |
| EN taal | ✅ | Compleet |
| FI taal | ✅ | Compleet |
| Mobile responsive | ✅ | < 768px geoptimaliseerd |
| Vercel deploy | ✅ | Live op productie URL |
| SEO meta tags | ✅ | Title, description |
| Accessibility | ✅ | ARIA labels, contrast |
| Performance | ✅ | ~46KB, geen externe JS libs |

---

## 🚦 STATUS

**Huidige versie:** 1.0.0  
**Status:** Production Ready ✅  
**Laatste deploy:** 9 februari 2026  
**Git branch:** newsec-valuation  

---

*Einde CLAUDE.md documentatie*
