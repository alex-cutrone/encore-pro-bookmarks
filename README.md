# Encore Pro · Internal Links

A single-page internal bookmarks dashboard for the Encore Pro team. No backend required — runs entirely in the browser and stores data in `localStorage`.

## Features

- **Category tabs**: Filter bookmarks by Product, Growth, Operations, or Client Success
- **Auto icons**: Pulls brand icons from [logo.dev](https://logo.dev) using the domain
- **Admin panel**: Add, edit, and delete bookmarks without touching code
- **Multi-category**: A single bookmark can belong to multiple categories
- **Zero dependencies**: One HTML file, no build step needed

## Setup

### GitHub Pages

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)` folder
4. Your site will be live at `https://[org].github.io/[repo-name]`

### Local

Just open `index.html` in a browser. That's it.

## Usage

**Viewing bookmarks**
- Use the category tabs to filter
- Click any card to open the link in a new tab

**Managing bookmarks (Admin)**
- Click the **Admin** button in the top right
- Fill in Name, URL, and select one or more categories
- The icon preview shows what logo.dev will pull for that domain
- Hit **Save** — done

**Data storage**
Bookmarks are saved in `localStorage` under the key `ep_bookmarks_v1`. They persist across sessions in the same browser. If you want to pre-populate or export bookmarks, open the browser console and run:

```js
// Export
copy(localStorage.getItem('ep_bookmarks_v1'))

// Import (paste a JSON array)
localStorage.setItem('ep_bookmarks_v1', '[...]')
```

## Customization

**Categories** — Edit the `CATEGORIES` array near the top of the `<script>` block in `index.html`:
```js
const CATEGORIES = ['Product', 'Growth', 'Operations', 'Client Success'];
```

**Default seed bookmarks** — Edit `getSeedData()` in the script to change what shows up on first load (before any admin changes).

**Colors** — All colors use CSS custom properties at the top of the `<style>` block. The `--accent` variable controls the gold highlight color.

## Icon service

Icons are fetched from [logo.dev](https://logo.dev) using a free-tier API key baked into the URL. If an icon fails to load, the bookmark falls back to the first letter of the name. You can swap to [Brandfetch](https://brandfetch.com) or [Clearbit](https://clearbit.com/logo) by changing the `iconUrl()` function.
