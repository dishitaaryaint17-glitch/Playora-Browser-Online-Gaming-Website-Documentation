# Build a Browser-Based Gaming Website - Playora

# Context

Build a modern browser-based gaming website called **Playora** that lets visitors instantly discover and play a curated collection of HTML5 games directly from their web browser.

The goal is to create a polished, fast, and visually engaging gaming hub where casual gamers can find and play games within two clicks of landing - no downloads, no sign-ups, no friction.

The website should prioritize:

- instant play
- speed and mobile responsiveness
- visual playfulness
- clean and maintainable code
- easy content management through an admin panel

This is not a social platform, not a game development tool, and not a subscription service.

The final site should feel like a modern, friendly gaming website rather than a corporate dashboard or an app store.

All branding, game thumbnails, game metadata, categories, and content will be:

- provided by the client before development begins

Only commercially usable assets may be used in the build.

---

# Goal

Build a browser-based gaming website branded as:

```text
Playora - Discover. Play. Repeat.
```

The site must:

1. Display a curated catalog of 50-100 HTML5 games across 6 categories.
2. Let any visitor click a game and play it instantly inside the browser.
3. Sort and filter games by category and search by title without page reloads.
4. Persist recently played and favorite games using browser local storage.
5. Provide a secure admin dashboard for full content management.
6. Run smoothly on desktop, tablet, and mobile devices.
7. Be deployment-ready on standard web hosting with no special server requirements.

The site should be fully usable without any sign-up or account creation.

---

# Site Structure Requirements

Build exactly:

```text
6 page templates + 4 static pages
```

The site must follow this structure:

## Page 1 - Home Page (`index.html`)

Include:

Title:

```text
Playora - Discover. Play. Repeat.
```

Requirements:

- top navigation bar with logo, 6 category links, and a search bar
- hero banner with tagline and a primary "Play Now" CTA
- "Featured Games" row
- "Trending Games" row
- "New Arrivals" row
- "Popular Categories" grid of 6 category tiles
- "Browse All Games" section
- footer with About, Contact, Privacy, Terms links

Avoid:

- pop-ups or modals on landing
- auto-playing audio or video

---

## Page 2 - Browse All Games (`games.html`)

Show:

- full game catalog in a responsive grid
- category filter tabs and search input that filter the grid in real time
- sort options: Trending, Newest, A-Z
- breadcrumb showing `Home > All Games`

Requirements:

- client-side filtering only - no page reloads
- grid that reflows from 4 columns on desktop to 2 columns on tablet to 1 column on mobile
- empty-state message if no games match the search or filter
- no server-side filtering

Do NOT include:

- mandatory pagination for initial launch (catalog fits comfortably)
- backend search endpoints

---

## Page 3 - Category Page (`category.html?cat=puzzle`)

Show:

- filtered grid of game cards based on the `cat` URL parameter
- category title and short description at the top
- search input that filters the visible grid in real time
- breadcrumb showing `Home > Category Name`

Requirements:

- client-side filtering only
- grid that reflows from 4 columns on desktop to 2 columns on mobile
- empty-state message if no games match

Do NOT include:

- pagination
- server-side filtering

---

## Page 4 - Game Detail Page (`game.html?slug=space-shooter`)

Include the actual playable game.

Layout:

- one AdSense banner above the iframe
- game embedded in a 16:9 iframe at the top
- fullscreen toggle button on the iframe
- game title, short description, and controls hint below
- "More Like This" strip of 4 related game cards
- favorite toggle and recently played tracking controls

Requirements:

- game must load within 3 seconds on a 4G connection
- fullscreen must work on iOS Safari, Chrome Android, and desktop browsers
- fire GA4 `game_start` event on iframe load
- fire GA4 `game_end` event on tab close or game change
- favorite and recently played state must be persisted in `localStorage`

---

## Page 5 - Recently Played (`recently-played.html`)

Show:

- grid of games pulled from `localStorage`
- up to 20 most recently played titles
- empty-state illustration with a CTA if history is empty
- option to clear all history

---

## Page 6 - Favorites (`favorites.html`)

Show:

- grid of games the user has starred
- empty-state illustration with a CTA if the list is empty
- option to remove individual games or clear all favorites

---

## Static Pages (About, Contact, Privacy, Terms)

Include:

- one column, max-width 720 px
- same header and footer as the rest of the site
- pure text content with H1, H2, paragraph styling only

Requirements:

- privacy policy must disclose GA4 cookies and any analytics tools in use
- contact page uses a simple `mailto:` link only (no form)
- terms page covers acceptable use and disclaimer

---

# Admin Dashboard

Accessible at `/admin` behind a secure login page.

## Admin Login

Requirements:

- username and password authentication
- session timeout after inactivity
- no public registration - credentials configured during setup
- admin routes blocked from public indexing via `robots.txt`

## Admin Features

Include:

- view all games in a paginated table (title, category, status)
- add new game (form: title, slug, thumbnail, category, description, iframe URL)
- edit existing game (same form pre-filled)
- delete game with confirmation prompt
- upload and manage game thumbnails (validate type and size)
- manage categories (add, rename, reorder, remove)
- toggle featured games for the homepage featured row
- control trending game listings

Do NOT include:

- public-facing admin registration
- game analytics reporting inside the admin panel
- multi-user roles or permissions for V1

---

# Content Requirements

The site must:

- use short, casual headings
- avoid technical or corporate tone
- describe each game in under 60 words
- explain controls in one short line
- support quick scanning over deep reading

Each game card must:

- show a 320×180 px thumbnail
- show the game title (max 28 characters displayed)
- show one category badge
- show a favorite toggle icon
- link to the game detail page on click

Each game entry must include:

- title
- slug (URL-safe identifier)
- thumbnail image
- category
- short description (under 60 words)
- controls hint (one line)
- iframe or embed URL
- up to 4 related games (by category or manual selection)

### Not Allowed

- lorem ipsum in production
- game descriptions over 60 words
- long onboarding or marketing paragraphs
- multi-step explainer text

---

# Visual Requirements

Use visuals to support play, not decoration.

Allowed visuals:

- game thumbnails
- category badges
- icons (Lucide or equivalent permissive-license set)
- one logo wordmark
- one Open Graph card per page
- empty-state illustrations (unDraw or similar permissive license)

Suggested direction:

Home page:

- bold hero banner with tagline
- large rounded game cards with soft shadows
- colorful category tiles

Game page:

- dark surface behind the iframe to reduce glare
- minimal chrome around the player

Category page:

- consistent card sizing
- predictable hover state

Visual style must remain:

- playful
- modern
- consistent across pages

### Not Allowed

- decorative stock photos
- 3D renders
- animated GIFs in the layout (only inside game iframes)
- mascots or characters that distract from games

---

# Design Requirements

Visual style:

- modern
- colorful
- clean
- mobile-first

The site should resemble:

- a polished casual gaming website 
- a well-organized game discovery hub
- something between Poki and a curated indie game catalog

Avoid:

- casino or gambling aesthetics
- enterprise dashboard layouts
- cluttered sidebars
- dark-pattern monetization

---

# Typography Requirements

Use clean, readable fonts only.

Recommended:

Display / headings:

- Poppins
- Montserrat

Body text:

- Inter
- Roboto

Requirements:

- single display font + single body font (max two families)
- consistent size scale: 12, 14, 16, 20, 24, 32, 48
- visible body text at all viewport sizes
- minimum 16 px body on mobile
- use `font-display: swap` or self-host fonts

### Not Allowed

- script fonts
- decorative fonts
- handwritten fonts
- more than two font families

---

# Color Requirements

Use no more than:

```text
3 dominant brand colors
```

plus background and text neutrals.

Suggested palette:

| Usage      | Name           | HEX       |
| ---------- | -------------- | --------- |
| Primary    | Electric Violet | `#7C3AED` |
| Secondary  | Neon Cyan      | `#06B6D4` |
| Accent     | Amber Glow     | `#F59E0B` |
| Background | Dark Void      | `#0D0D1A` |
| Surface    | Card Dark      | `#1A1A2E` |
| Text       | Soft White     | `#F1F5F9` |

Requirements:

- WCAG AA contrast on all text
- consistent accent usage (Violet = CTA, Cyan = links/active states, Amber = badges and tags)
- dark theme by default for V1

### Not Allowed

- rainbow palettes
- neon clashes
- gradient overload
- inconsistent CTA colors

---

# Layout & Spacing Requirements

Pages must maintain:

- 12-column grid on desktop, 4-column on mobile
- 16 px base spacing scale
- max content width of 1280 px
- breathing room around game cards (gap ≥ 16 px)

Requirements:

- one primary CTA per visible fold
- consistent card sizing across pages
- header height fixed at 72 px desktop / 60 px mobile

### Avoid

- horizontal scroll on mobile
- overlapping cards
- inconsistent gutters
- text touching the screen edge

---

# Game Categories

The site must support exactly:

1. Action
2. Adventure
3. Racing
4. Puzzle
5. Sports
6. Arcade

---

# Responsiveness & Performance Requirements

Site must:

- pass Lighthouse Mobile Performance ≥ 85
- render first paint in under 2 seconds on 4G
- work on screens from 320 px wide upward
- load no more than 200 KB of JavaScript outside game iframes

Requirements:

- defer all non-critical scripts
- lazy-load game thumbnails below the fold
- self-host fonts or use `font-display: swap`
- no console errors on any page

---

# Personalization Requirements

## Recently Played

- automatically recorded when a user starts a game
- persisted in `localStorage` across sessions
- displays up to 20 most recent titles
- clearable by the user on the recently played page

## Favorites

- user taps a heart icon on any game card or detail page
- stored in `localStorage`
- appears on the `/favorites` page
- removable individually or all at once

## Continue Playing

- subset of recently played shown on the homepage
- highlights the last 3-4 games the user interacted with

---

# SEO Requirements

- SEO-friendly URLs (e.g. `/game/space-shooter`, `/category/puzzle`)
- unique `<title>` and `<meta description>` on every page
- Open Graph tags on game detail and category pages
- `sitemap.xml` covering all public-facing pages
- `robots.txt` blocking `/admin`
- canonical tags on filtered or parameterized views

---

# Analytics Requirements

Integrate on every page:

- Google Analytics 4 site tag

Custom GA4 events:

| Event | Trigger |
| -------------- | ---------------------------------- |
| `game_start` | Game iframe loads |
| `game_end` | User leaves game page |
| `category_click` | User selects a category |
| `search_used` | User submits a search query |
| `favorite_added` | User favorites a game |

Requirements:

- GA4 tag must fire on every page
- defer non-critical analytics scripts
- privacy policy must disclose all tracking tools in use

### Not Allowed

- pop-up ads
- redirect ads
- crypto mining scripts
- email harvesting

---

# Asset Usage Requirements

Client will provide:

- logo in PNG (transparent background)
- Website Reference image for UI

Developer will produce:

- all HTML, CSS, and JavaScript
- admin dashboard UI
- empty-state illustrations (unDraw or similar permissive license)
- `sitemap.xml` and `robots.txt`

Not Allowed:

- copyrighted brand assets
- watermarked or unlicensed game assets
- assets with unclear ownership

---

# Deliverables

Submit exactly:

## Live Website

Quantity:

```text
1
```

Accepted hosts:

- Vercel
- Netlify
- Cloudflare Pages
- Shared hosting (cPanel)
- VPS

---

## Source Code Repository

Quantity:

```text
1
```

Accepted formats:

- GitHub repository (public or private)
- a ZIP archive of the same repo

Must include:

- `README.md` with setup and deploy instructions
- complete `/games/` folder or `games.json` catalog file
- all HTML, CSS, JS, and admin files
- `sitemap.xml` and `robots.txt`

---

## Admin Credentials

Quantity:

```text
1
```

Delivered securely - never committed to the repository.

---

# Required Delivery Structure

```text
Playora_Website/

├── live/
│   └── live_url.txt

├── source/
│   ├── playora-repo/
│   │   ├── index.html
│   │   ├── games.html
│   │   ├── category.html
│   │   ├── game.html
│   │   ├── recently-played.html
│   │   ├── favorites.html
│   │   ├── about.html
│   │   ├── contact.html
│   │   ├── privacy.html
│   │   ├── terms.html
│   │   ├── admin/
│   │   │   ├── index.html
│   │   │   └── dashboard.html
│   │   ├── assets/
│   │   │   ├── css/
│   │   │   ├── js/
│   │   │   └── images/
│   │   ├── data/
│   │   │   └── games.json
│   │   ├── sitemap.xml
│   │   ├── robots.txt
│   │   └── README.md
│   └── playora-repo.zip

└── brand/
    ├── logo.svg
    ├── logo-512.png
    ├── logo-1024.png
    ├── favicon.ico
    └── og-card.png
```

---

# Scope Restrictions

Do NOT include:

1. User accounts, login, or sign-up (public-facing)
2. Multiplayer or real-time networking
3. Tournament system
4. Leaderboards or achievement system
5. Chat or friend system
6. Subscription plans or payment integration
7. Real-money gaming of any kind
8. Native iOS or Android apps
9. Multi-language support
10. AI-powered recommendations
11. Live streaming functionality
12. Social networking features
13. Email collection or newsletter forms
14. Pop-up ads or interstitial ads
15. Crypto or Web3 integrations
16. WordPress, Wix, or any third-party page builder
17. In-house game development

---

# Acceptance Criteria

Final delivery is accepted only when ALL of the following are true:

1. All pages load without console errors on Chrome, Firefox, Safari, and Edge.
2. At least 10 games are playable end-to-end on the live site.
3. Category filtering and search work client-side without page reloads.
4. Recently played and favorites persist correctly across sessions via `localStorage`.
5. Admin dashboard allows adding, editing, and deleting games behind authenticated login.
6. Lighthouse Mobile Performance ≥ 85.
7. First Contentful Paint under 2 seconds on simulated 4G.
8. GA4 `game_start` and `game_end` events fire correctly.
9. `sitemap.xml` covers all public-facing pages.
10. `robots.txt` blocks `/admin`.
11. About, Privacy Policy, Terms, and Contact pages are live.
12. `README.md` includes working setup and deploy instructions.
13. No horizontal scroll on any viewport from 320 px upward.
14. Fullscreen gameplay works on iOS Safari, Chrome Android, and desktop.

---

# Delivery Terms

Single-delivery project.

Revisions are not required unless:

- a listed deliverable is missing
- the admin dashboard cannot add, edit, or delete games
- the site fails to load on a mainstream browser
- GA4 events are not firing
- Lighthouse Mobile Performance falls below 70
- any acceptance criterion above is unmet at handover

Final delivery is accepted only after:

- live site is reachable at the provided URL
- complete source repository or ZIP is handed over
- admin credentials are delivered securely
- all acceptance criteria above are met

---

# Final Goal

The final result should function as:

```text
A clean, fast, and visually engaging browser gaming website that lets any
visitor discover and play HTML5 games instantly, while giving the owner
full control over the catalog through a simple admin panel.
```

The website should:

- load instantly on any modern device
- let any visitor play within two clicks of landing
- persist favorites and recently played games without requiring an account
- look modern and playful without looking childish
- remain deployable on a free or low-cost hosting tier
- serve as a real, usable product ready for launch
