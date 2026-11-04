# analog.design

A static site. No build step, no framework — just HTML files in folders.
Upload the contents of this folder to any static host and point analog.design at it.

## Layout

```
.htaccess               forces https, hides folder listings (Apache/GoDaddy)
index.html              the logo grid
favicon.svg
roam/
  index.html            one scrollable page: description → #support → #privacy
  sphere.svg            the mark used on the grid
  wordmark.svg          the horizontal mark at the top of the roam page
  icon.png              app icon (kept for the favicon)
  privacy/index.html    redirect → /roam/#privacy   (old URL, safe to give to Apple)
  support/index.html    redirect → /roam/#support
golfa/
  index.html            one scrollable page: description → #privacy → #terms
  assets/golfer.svg     the mark used on the grid
  assets/golfa-logo.svg full logo, used on the golfa page
  privacy/index.html    redirect → /golfa/#privacy
```

Folder + `index.html` means the URLs are clean: `analog.design/roam/`,
`analog.design/roam/#privacy`, and so on. The "analog design" wordmark at the
bottom of every page links back to the grid.

## Adding a project

1. Make a folder: `myapp/`, with an `index.html` — copy `roam/index.html` or
   `golfa/index.html` and swap in your text. Keep the legal/support text in
   `<section id="…">` blocks below the description; that's the whole page.
2. Drop the logo SVG in the folder.
3. In the root `index.html`, copy one of the `<a class="logo">` blocks inside
   `<nav class="grid">`, point it at `/myapp/` and the logo, and add a
   `.logo.myapp img { width: …px; }` rule so it sits at the same visual
   weight as the others.

Logos show greyed-out and desaturated until hovered; the grid reflows on its
own (2 across on a phone).

## Hosting on GoDaddy (Web Hosting / cPanel)

1. GoDaddy → My Products → **Web Hosting** → Manage → **cPanel Admin**.
2. Files → **File Manager** → open **public_html**.
   (If GoDaddy put a placeholder `index.html` or `coming-soon` page there,
   delete it first.)
3. Click **Upload**, choose `analog-design-site.zip`, wait for it to finish.
4. Back in File Manager, right-click the zip → **Extract** → extract into
   `public_html`. Then delete the zip.
5. Make sure `.htaccess` is in `public_html` alongside `index.html`.
   File Manager hides dot-files by default — Settings (top right) →
   "Show Hidden Files (dotfiles)".
6. Visit https://analog.design. Done.

If analog.design was registered with GoDaddy and is on the same account, it
is usually already pointed at the hosting; otherwise set the domain's A
record to the hosting IP shown on the Web Hosting dashboard.

To update later: upload the changed file(s) into the same folders and
overwrite. No build step.

**Note:** this is for GoDaddy *Web Hosting* (the cPanel product). GoDaddy's
*Website Builder* is a drag-and-drop editor and cannot host uploaded HTML.

## Other hosts

Any static host serves it as-is: Cloudflare Pages, Netlify (drag the folder
onto the dashboard), or GitHub Pages (push, enable Pages, add a `CNAME` file
containing `analog.design`).
