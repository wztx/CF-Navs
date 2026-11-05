<div align="center">
  <img src="../../public/icon.png" alt="CF-Navs Project Icon" width="112" height="112">
  <h1>CF-Navs</h1>
  <p><strong>Consolidate your frequently used websites, work tools, and private favorites into your own homepage.</strong></p>
  <p>Runs on Cloudflare Workers, requiring no self-hosted server. Import existing bookmarks, choose a theme, and access the same navigation space on both your computer and mobile device.</p>

  <p>
    <img src="https://img.shields.io/badge/Cloudflare-Workers-F38020?logo=cloudflare&logoColor=white" alt="Cloudflare Workers">
    <img src="https://img.shields.io/badge/Svelte-5-FF3E00?logo=svelte&logoColor=white" alt="Svelte 5">
    <img src="https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white" alt="TypeScript 5">
    <a href="../../LICENSE"><img src="https://img.shields.io/badge/License-Apache--2.0-2563EB" alt="Apache License 2.0"></a>
  </p>

<p>
    <a href="#功能">Features</a> ·
    <a href="#界面预览">Interface Preview</a> ·
    <a href="#快速部署">Quick Deployment</a> ·
    <a href="#本地开发">Local Development</a> ·
    <a href="../../docs/README.md">Project Documentation</a>
  </p>

  <a href="https://github.com/lbjxr/CF-Navs/fork">
    <img src="https://img.shields.io/badge/Fork_on_GitHub-181717?logo=github&logoColor=white" alt="Fork on GitHub">
  </a>
  <a href="https://github.com/lbjxr/CF-Navs">
    <img src="https://img.shields.io/badge/%E2%AD%90_Star-FFC107?style=flat" alt="Star this project on GitHub">
  </a>
</div>

**Languages:** [简体中文](../../README.md)

---

## Features

**The more you save, the faster you can find and organize them.** CF-Navs combines two-level categorization, site-wide search, batch organization, and data backup, making it suitable as a personal start page, a work toolbox, or a public resource navigator. Visitors can browse public content, while administrators can manage all bookmarks after logging in, without needing to maintain a separate site for private links.

| | Capability | Description |
|---|---|---|
| ☁️ | Full-Stack Edge Hosting | Host entire sites with Workers, D1, and KV. Your code and data remain under your own GitHub / Cloudflare account, with no need to rent a VPS or maintain database services. |
| 🧭 | Navigation Homepage | Primary groups and secondary categories are clearly presented, supporting search by title, URL, description, and full category path. Left, top, and mobile navigation adapts to different screens, and the top navigation can be displayed across multiple lines. |
| 🏠 | Homepage Settings | The site title, search box, search engine selector, and number of “Frequent Visits” are all configurable, with real-time preview before saving. After logging in, you can directly create top-level and subcategories on the homepage. |
| 🛠️ | Backend Management | Edit, move, reorder at the same level, and protect categories from deletion. Full path location and bulk movement of bookmarks reduce the need for one-by-one editing. Site, layout, search, backup, and account security are centrally managed. |
| 🔒 | Private Bookmarks | New or edited bookmarks can be marked as “Private Links (visible only to logged-in users).” Regular visitors will not receive data for private bookmarks, while administrators can view and manage them normally after logging in. |
| 🗂️ | Private Categories | Categories can be set to “Hidden from visitors (visible only to logged-in users).” Visitors will not see the category, its subcategories, or the bookmarks within them, but administrators can still manage them normally after logging in. |
| ↕️ | Cross-Category Reordering | Supports moving bookmarks between top-level, subcategories, and empty categories, as well as adjusting order within a category. Use drag-and-drop on PC, or the “Move to Category” option on mobile, with unified save or cancel actions. |
| 🔄 | Browser Bookmark Sync | One-way sync can be enabled in the backend. After adding a bookmark, the Chrome/Edge extension displays a floating category panel in the upper-right corner of the current page. Click the extension icon to show or hide it. You can edit the title and URL before confirmation, without altering the category structure or deleting bookmarks on the navigation page. |
| 📊 | Access Analytics | Clicks on homepage bookmarks are counted. The backend provides statistics on total clicks, visited vs. unvisited bookmarks, a Top 20 ranking of most-visited bookmarks, and paginated lists of unvisited bookmarks. The latest data is refreshed when you enter the analytics page. |
| 🎨 | Appearance Customization | Includes 22 built-in themes, light/dark modes, background and accent colors, and separate font size and icon size settings for top-level and subcategories. Card size, transparency, and footer HTML / CSS / JavaScript are all customizable. CSS and footers support isolated previews. |
| 🔎 | Search & Icons | Full-site group search, configurable external search engines, and support for displaying bookmark Favicons / Iconify icons, category images, text, and emoji icons. |
| 💾 | Data Migration | Export backups in full or by category, optionally including site settings. JSON files can be appended, merged, or overwritten during restoration, and are compatible with Sun-Panel data and browser bookmark HTML. |
| 🔐 | Security & Authentication | PBKDF2 password hashing, Bearer Session Tokens, CSP, admin API authentication, and rate limiting for failed login attempts. Private icons have access control and isolated caching. |
| ⚡ | Loading Optimization | Code splitting, edge caching, local snapshots, lazy loading of icons, and basic PWA offline fallback. Direct refreshes from the backend will not cause a brief flash of the homepage. |

Prefer a compact layout? The minimum width for desktop detail cards can be set to **40 px**, while mobile devices still maintain a safe minimum of **150 px**. Extremely narrow cards will compress the title and description, making them more suitable for icon-based navigation.

### Bookmark Privacy and Cross-Category Sorting

- **Direct Organization on the Home Page**: After logging in, you can create a new top-level category or a new subcategory under the current group; the new category will be automatically selected. When editing a bookmark, the category selector will expand and highlight the current category, reducing the need for repeated searching.
- **Private Links**: When adding or editing a bookmark, an administrator can check the box for "Set as private link (visible only to logged-in users)." Public data interfaces for unauthenticated visitors will filter out such bookmarks. Administrators can still view, edit, and delete them on the home page and in the admin panel after logging in.
- **Private Categories**: When editing a category in the admin panel, an administrator can check the box for "Hidden from visitors (visible only to logged-in users)." Unauthenticated visitors will not receive data for this category, its subcategories, or the bookmarks within them. Administrators can still view and manage them normally after logging in. Existing categories remain visible to visitors by default.
- **Drag-and-Drop Across Categories**: After logging in, an administrator can click "Sort" in any category on the home page to enter a unified sorting session. On PC, you can drag bookmarks into top-level, second-level, or empty categories and adjust their positions. On mobile, you can use the "Move to category" option to select a destination. Clicking "Save Sort" at the bottom saves all category changes and reorderings at once. Clicking "Cancel" discards the current changes.
- **Bulk Moving**: When a large number of bookmarks need to be reorganized, you can filter and select multiple bookmarks in the admin panel, then choose a target category and confirm the full path to move them all at once, without having to open each one for editing.
- **Browser Bookmark Synchronization**: To enable "Browser Bookmark Synchronization," go to "Settings → Site Settings" in the admin panel, then install the Chrome/Edge extension from [`browser-extension`](../../browser-extension/) and log in. On the extension's home page, when a navigation page is already connected, the address, account, and password input fields are hidden by default. Click "Modify Login Information" to expand and edit them. The fields will automatically expand if the session has expired or if no connection has been established yet. After this, when you add a new web bookmark, a category hover window will appear in the top-right corner of the current page, allowing you to edit the title and URL before confirmation. Click the extension icon to show or hide the panel, or click anywhere outside the panel on the webpage to collapse it. After confirmation, the bookmark is synchronized to the selected top-level or second-level category, and an icon candidate of `https://favicon.im/<hostname>?larger=true` is saved according to the default icon strategy. Unconfirmed bookmarks remain in the pending synchronization queue, where you can select, postpone, or manually delete them from the pending list. The list will dynamically mark entries that no longer exist in your browser's bookmarks. The extension does not create navigation categories based on browser bookmark folders; it only performs a one-way addition from "Browser → Navigation Page" and will not delete or overwrite existing bookmarks on the navigation page. Users who have already installed the extension should please reload it and refresh the webpage according to the [Extension Update Instructions](../../browser-extension/README.md#更新已安装的扩展).

## Interface Preview

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Light Home Page</strong><br>
      <img src="../../docs/screenshots/cf-navs-light.webp" alt="CF-Navs Light Home Page: Eye Protection vs. Frosted Glass Diagonal Comparison">
    </td>
    <td align="center" width="50%">
      <strong>Dark Home Page</strong><br>
      <img src="../../docs/screenshots/cf-navs-dark.webp" alt="CF-Navs Dark Home Page: Eye Protection vs. Frosted Glass Diagonal Comparison">
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <strong>Light Mode (Mobile)</strong><br>
      <img src="../../docs/screenshots/cf-navs-light-mobile.webp" alt="CF-Navs Light Home Page (Mobile): Eye Protection vs. Frosted Glass Diagonal Comparison" width="260">
    </td>
    <td align="center" width="50%">
      <strong>Dark Mode (Mobile)</strong><br>
      <img src="../../docs/screenshots/cf-navs-dark-mobile.webp" alt="CF-Navs Dark Home Page (Mobile): Eye Protection vs. Frosted Glass Diagonal Comparison" width="260">
    </td>
  </tr>
</table>

<p align="center">
  <strong>Theme and Site Settings</strong><br>
  <img src="../../docs/screenshots/cf-navs-admin-setting.webp" alt="CF-Navs Theme and Site Settings">
</p>

More interface screenshots are located at [`docs/screenshots`](../../docs/screenshots).

## Quick Deployment

**Don't want to bother with servers? We recommend starting with a console deployment.** Prepare your GitHub and Cloudflare accounts, then complete the deployment by following "Fork → Associate Repository → Set Installation Token → Initialize via Web". A normal installation does not require manually executing SQL or entering a Cloudflare API Token. If Workers Builds / Git import is unavailable, you can use the [GitHub Actions Alternative Deployment](../../docs/guides/DEPLOYMENT.md#方式三github-actions备选); by default, associating a Cloudflare account is still recommended.

You can start with the free plan from Cloudflare, but the free tier is not unlimited; there are quotas for requests, databases, and KV operations. For details, please refer to the official documentation for [Workers](https://developers.cloudflare.com/workers/platform/pricing/), [D1](https://developers.cloudflare.com/d1/platform/pricing/), and [KV](https://developers.cloudflare.com/kv/platform/pricing/).

When using for the first time, please select a deployment method and complete the entire process. Do not mix the two procedures. Regardless of the method used, the database and administrator account will ultimately be initialized via `/install`.

### Self-hosted (Docker)

You can also self-host without using Cloudflare: this repository also provides a Node + SQLite
Docker deployment (runtime is in `server/`, deployment assets are in `docker/`). The application features are
identical to the Cloudflare version, and there is a ready-made import tool for migrating data from Cloudflare:

```bash
git clone https://github.com/lbjxr/CF-Navs.git
cd CF-Navs/docker
```

For deployment, reverse proxy, data migration, backup and recovery, and security boundaries, see
[DOCKER_DEPLOY.md](../../docs/guides/DOCKER_DEPLOY.md).

CF-Navs requires the following Cloudflare resources:

| Resource | Binding Name | Purpose |
|---|---|---|
| D1 Database | `DB` | Stores settings, categories, and bookmarks |
| KV Namespace | `SESSION` | Login rate limiting, click rate limiting, and session revocation list |
| Secret | `SETUP_TOKEN` | Manual configuration for authorizing the initial installation |

### Method 1: Deploy via the Cloudflare Console (Recommended)

Suitable for users who want to perform all operations in the browser and do not wish to install local tools. After Cloudflare links to your GitHub Fork, it will automatically build and deploy from the `main` production branch; when synchronizing upstream updates in the future, please also update this branch.

#### Step 1: Fork this repository and give it a Star

[![Fork on GitHub](https://img.shields.io/badge/Fork-GitHub-181717?style=for-the-badge&logo=github)](https://github.com/lbjxr/CF-Navs/fork)
[![Star this project on GitHub](https://img.shields.io/badge/%E2%AD%90_Star-FFC107?style=for-the-badge)](https://github.com/lbjxr/CF-Navs)

Click the **Fork** button at the top to create a copy of this repository; after opening the repository's homepage, click **Star** in the upper right corner to follow project updates.

#### Step 2: Deploy to Cloudflare Workers

[![Deploy to Cloudflare Workers](https://img.shields.io/badge/Deploy-Cloudflare%20Workers-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://dash.cloudflare.com/?to=/:account/workers-and-pages)

Click the button above to go to Cloudflare, then select Connect to GitHub. After authorizing, choose the project you just forked.

<img width="1600" height="1000" alt="Select Project" src="../../docs/screenshots/cf-deploy-select-repo.webp">

After clicking **Start Setup**, confirm the following values in the build configuration (you can leave the rest as default):

- Build command: `npm run build`
- Deployment command: `npx wrangler deploy`
- The production branch `main`, root directory `/`, and Node.js environment are automatically detected by [`wrangler.toml`](../../wrangler.toml); to specify a Node.js version, set `NODE_VERSION=24` in **Build Variables** ([official documentation](https://developers.cloudflare.com/workers/ci-cd/builds/build-image/))

<img width="1600" height="1000" alt="Build Settings" src="../../docs/screenshots/cf-deploy-build-settings.webp">

#### Step 3: Save and complete the first production deployment

Save and complete the first **Production** deployment. Under normal circumstances, Cloudflare will create and bind the `DB` D1 database and the `SESSION` KV namespace based on [`wrangler.toml`](../../wrangler.toml).

After the initial deployment, you should see these two bindings. If you encounter a `missing binding` error or an error about insufficient permissions to create resources, first confirm that the deployment is coming from the **Production** environment on the `main` branch, that Cloudflare is currently using the correct account, and consult [Troubleshooting](../../docs/guides/TROUBLESHOOTING.md); do not repeatedly create the database or KV without confirming the account and resources.

#### Step 4: Configure the SETUP_TOKEN secret

After the first production deployment is complete, select **Production Environment** under **Settings → Variables and Secrets** in the Worker, and configure `SETUP_TOKEN`:

- If the list already contains a `SETUP_TOKEN` automatically generated by Cloudflare, edit it and replace it with the value you saved, then perform a **clear cache** in **Settings → Build**.
- If what you have is a plain text variable instead of a secret, delete it and re-add a `SETUP_TOKEN` of type **Secret**. Do not keep both a plain text variable and a Secret with the same name.
- If the list does not contain a `SETUP_TOKEN`, manually add a variable of type **Secret**. Use a sufficiently long random string for the value; do not add it as a plain text variable.

<img src="../../docs/screenshots/cf-deploy3.jpg" alt="Cloudflare Console Variable and Secret Settings Example">

#### Step 5: Redeploy to apply the Secret

After saving the Secret, redeploy the same `main` production deployment: you can perform **Retry/Redeploy** on the latest production deployment on the **Deployments** page, or push a new commit to `main`. Do not simply access `/install` right after saving the Secret; you must first allow the new deployment to read the Secret.

#### Step 6: Visit /install to complete the installation

Open the deployed Workers URL and navigate to `/install`. Enter the `SETUP_TOKEN` value currently configured in your production environment, then create an administrator username and password. After confirming that the installation and login are successful, delete or rotate this token; regardless of whether it was originally auto-generated by Cloudflare or added by you manually, a site that has completed installation no longer needs it.

Using a custom domain is optional: first, add and enable the custom domain under **Domains and Routes**, confirm that it is accessible and that you can log in successfully, and then disable the `workers.dev` address as needed. If you are not yet ready for a custom domain, please keep the Workers URL and do not disable the default access endpoint prematurely.

### Method 2: Deploy with Wrangler CLI

Prerequisites: Node.js **22.12+ (22.x) or 24+**, npm, and a Cloudflare account. Node.js 24 LTS is recommended. All resource commands will act on the account currently logged in to Wrangler; if you have multiple Cloudflare accounts, first use `npx wrangler whoami` to confirm your account.

```bash
git clone https://github.com/lbjxr/CF-Navs.git
cd CF-Navs
git switch develop
npm install

npx wrangler login
npx wrangler whoami

# The following two create commands should only be executed once if the resources do not already exist
npx wrangler d1 create cf-navs-db
npx wrangler kv namespace create SESSION

npm run setup:wrangler
npm run deploy                 # Initial deployment: create the Worker first
npx wrangler secret put SETUP_TOKEN
npm run deploy                 # Redeploy after the secret takes effect
```

If the D1 database or KV namespace already exists, do not run the `create` command again. First, use `npx wrangler d1 list` and `npx wrangler kv namespace list` to confirm the resources in your current account, then run `npm run setup:wrangler`. The D1 database name should be `cf-navs-db`, and the KV binding name for the Worker should be `SESSION`.

`npm run setup:wrangler` will write the real resource ID to `wrangler.local.toml`, which is ignored by Git. After deployment is complete, visit `/install` to have the installer initialize the database structure and create an administrator. Do not run `wrangler secret put` before the initial deployment is finished, as the Worker has not yet been created.

A normal installation does not require manually executing SQL. Only when the installer reports a failure in schema initialization should you use [`schema.sql`](../../schema.sql) or `npm run db:init:remote` to recover.

### Post-deployment checks applicable to both methods

- `/install` can be opened, and initialization can be completed using `SETUP_TOKEN`.
- You can log in to the backend with the newly created administrator account.
- Categories and bookmarks can be saved normally; the data remains after refreshing the page.
- If the page still shows the old version, force-refresh it first to let the new Service Worker take over.
- If installation or binding fails, check the Worker logs: `npx wrangler tail`. Before running any commands that involve online data, confirm your current Cloudflare account and the target Worker.

**Get your navigation page up and running in no time**: Import an existing set of bookmarks in the backend, choose a theme, set the categories or links you want to hide, and then set the site as your browser's homepage. Afterwards, you can use the browser extension to collect new bookmarks and keep everything organized by sorting them on the homepage or moving them in bulk through the backend.

For more configuration and troubleshooting, please read the following documentation; for deployment branches and Node.js requirements, please follow the instructions on this page:

- [Quick Start](../../docs/guides/QUICKSTART.md)
- [Complete Deployment Guide](../../docs/guides/DEPLOYMENT.md)
- [Common Issues and Troubleshooting](../../docs/guides/TROUBLESHOOTING.md)

## Local Development

The development environment uses Node.js 22.12+ (22.x) or 24+, with Node.js 24 LTS (consistent with the CI environment) recommended.

Install dependencies:

```bash
npm install
```

Start the Worker and front-end development services separately:

```bash
# Terminal 1
npm run dev

# Terminal 2
npm run dev:web
```

The default front-end address is `http://localhost:5173`.

Common checks:

```bash
npm run type-check
npm test
npm run build
git diff --check
```

## Technology Stack

| Level | Technology |
|---|---|
| Frontend | Svelte 5, TypeScript, Vite 7 |
| Worker API | Hono, Cloudflare Workers |
| Data & Session | Cloudflare D1, Cloudflare KV |
| Interaction & Sorting | SortableJS |
| Testing | Vitest 4, Svelte Check, real Chrome regression script |

## Project Structure

```text
CF-Navs/
├── src/                 # Svelte pages, components, and browser-side logic
├── worker/              # Worker routing, middleware, and D1 data access
├── shared/              # Shared types and contract settings for frontend and backend
├── public/              # Icons, PWA, and other static resources
├── browser-extension/   # Chrome/Edge browser extension for bookmark synchronization
├── tests/               # Vitest unit and regression tests
├── docs/                # User guide, technical reference, and screenshots
├── scripts/             # Development, deployment, and audit scripts
├── schema.sql           # D1 database structure
└── wrangler.toml        # Cloudflare Worker public configuration
```

The architecture, API, and performance contracts can be found in the [project documentation index](../../docs/README.md).

## Environment Configuration

| Name | Type | Required | Description |
|---|---|---|---|
| `DB` | D1 binding | Yes | Database binding |
| `SESSION` | KV binding | Yes | Stores login/click rate limits and session revocation lists |
| `SETUP_TOKEN` | Secret | First-time installation | Authorizes `/install`; it is recommended to delete or rotate it after a successful installation |
| `SESSION_TTL` | Variable | No | Session validity period. The default in `wrangler.toml` is `2592000` seconds (30 days); if not set, the Worker falls back to 7 days |
| `INIT_ADMIN_USER` | Variable | No | For upgrading old databases or recovering credentials only |
| `INIT_ADMIN_PASSWORD` | Secret | No | For upgrading old databases or recovering credentials only |
| `RESET_ADMIN_CREDENTIALS` | Variable | No | A one-time flag used to forcibly reset credentials in an old database |

Do not write real resource IDs, passwords, Tokens, or other Secrets into the repository.

## Data Import

No need to re-enter data that has already been favorited. The backend supports the following data formats:

- **CF-Navs JSON Backup**: Supports exporting all data or by category, preserving a two-level category hierarchy. You can also choose whether to include site settings. During import, it supports appending and merging by full path or restoring by overwriting.
- **Sun-Panel Data**: Imports categories at the first level and converts bookmark and compatible icon fields, so migrating existing navigation doesn't require starting from scratch.
- **Browser Bookmark HTML**: Imports standard files exported from browsers. Valid folders are mapped to a two-level category structure, and deeper paths are flattened into second-level headings.

**Move only the part you need**: You can export a main category along with its subcategories, or select only a second-level category. The system will automatically fill in the necessary parent category records without including bookmarks from unselected categories. This is suitable for migrating a set of work resources to another CF-Navs instance, or for keeping a separate backup for key categories.

Before importing, please back up your existing data: **Append mode retains duplicate links, while overwrite mode replaces all categories and bookmarks**. Partial exports are a backup and migration feature, not an automatic deduplication or two-way synchronization tool; backups may contain private links and site settings, so please store them securely.

See [Sun-Panel Data Import](../../docs/guides/SUNPANEL_IMPORT.md) and [Browser Bookmark Import](../../docs/guides/BROWSER_BOOKMARK_IMPORT.md).

## Contributing

Welcome to provide feedback on your experience via Issues and contribute improvements via Pull Requests. Before you begin, please read [Contributing](../../CONTRIBUTING.md) and complete validation based on the scope of your changes. For security issues, please use the [private reporting channel](../../SECURITY.md) and do not paste credentials or private bookmarks in public Issues.

## Acknowledgments

The project references the design concepts of [Sun-Panel](https://github.com/hslr-s/sun-panel), and some of its icon-fetching logic was inspired by [iori-nav](https://github.com/jy02739244/iori-nav).

## Star History

<a href="https://www.star-history.com/?repos=lbjxr%2FCF-Navs&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=lbjxr/CF-Navs&type=date&theme=dark&legend=top-left&sealed_token=7kyATdN3x5tJ6WJAhA5MwxWL93j-C9ZnSxJli_vTqztkkZF54Sp95nJzSMW-Xggc19KoraDrqDNjCWN6VuQrSEmOX8CAbyYqMi0I_6K3DS2GEr0x1rgf8VDa2kBJIgOP74JqDldlCFRRbGGNjvrDVJ12e4SIShmH78leu6Vxg6WQzidKg4PULPCzlwi-" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=lbjxr/CF-Navs&type=date&legend=top-left&sealed_token=7kyATdN3x5tJ6WJAhA5MwxWL93j-C9ZnSxJli_vTqztkkZF54Sp95nJzSMW-Xggc19KoraDrqDNjCWN6VuQrSEmOX8CAbyYqMi0I_6K3DS2GEr0x1rgf8VDa2kBJIgOP74JqDldlCFRRbGGNjvrDVJ12e4SIShmH78leu6Vxg6WQzidKg4PULPCzlwi-" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=lbjxr/CF-Navs&type=date&legend=top-left&sealed_token=7kyATdN3x5tJ6WJAhA5MwxWL93j-C9ZnSxJli_vTqztkkZF54Sp95nJzSMW-Xggc19KoraDrqDNjCWN6VuQrSEmOX8CAbyYqMi0I_6K3DS2GEr0x1rgf8VDa2kBJIgOP74JqDldlCFRRbGGNjvrDVJ12e4SIShmH78leu6Vxg6WQzidKg4PULPCzlwi-" />
 </picture>
</a>

## License

This project is licensed under the [Apache License 2.0](../../LICENSE). For project attribution information, see [`NOTICE`](../../NOTICE).

### Fork and Ownership Notes

If you fork, redistribute, or release modified versions based on CF-Navs, please:

- Retain the `LICENSE`, `NOTICE`, and any existing copyright, license, and attribution statements from the source files.
- As required by the Apache License 2.0, include clear modification notes in any modified files.
- Clearly state in the README or product documentation that the project is based on CF-Navs, and link to the upstream repository; do not imply that the modified version is officially released or endorsed by the original project authors.

The above instructions are for helping users identify derivative versions; the specific licensing rights and obligations are subject to [LICENSE](../../LICENSE).

<!-- Aifadian Sponsorship Section (Collapsible Card) -->
<hr>

<div align="center">

<details>
  <summary><b>☕️ Like CF-Navs? Buy the author a coffee / Sponsor</b></summary>
  <br>
  <p>If this project has been helpful to you, feel free to show your support with a sponsorship! Your support is the greatest motivation for keeping the project updated and maintained ❤️</p>
  <a href="https://afdian.com/a/benjian" target="_blank">
    <img src="https://img.shields.io/badge/爱发电-前往赞助-946CE6?style=for-the-badge&logo=afdian&logoColor=white" alt="爱发电赞助">
  </a>
  <p><small>💡 Sponsorship includes setup assistance. For details, please see the Afdian homepage.</small></p>
</details>

</div>
