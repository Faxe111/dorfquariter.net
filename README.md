# Dorfquartier static website

Static rebuild of `https://dorfquartier.net/` for GitHub Pages.

## What is included

- Clean static pages: `index.html`, `bilder.html`, `preise.html`, `anfahrt-kontakt.html`
- Local CSS in `assets/styles.css`
- Downloaded public images in `assets/images/`
- Original captured source pages and assets in `source-crawl/` for reference
- `CNAME` set to `dorfquartier.net` for GitHub Pages custom-domain hosting

## Local preview

Open `index.html` in a browser, or run:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Publish on GitHub Pages

1. Create a new GitHub repository, for example `dorfquartier`.
2. Push this folder to the repository:

```bash
git remote add origin git@github.com:YOUR-USER/dorfquartier.git
git branch -M main
git push -u origin main
```

3. In GitHub: Settings → Pages → Build and deployment → Deploy from a branch.
4. Select branch `main` and folder `/root`, then save.
5. In GitHub Pages custom domain, enter `dorfquartier.net`.

## DNS at Strato

Keep the domain at Strato, but point DNS to GitHub Pages.

For the root domain `dorfquartier.net`, use GitHub Pages A records:

```text
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

If Strato supports AAAA records, also add:

```text
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

For `www.dorfquartier.net`, add a CNAME to `YOUR-USER.github.io`.

Do not cancel the current Strato homepage package until GitHub Pages shows the custom domain as verified and the site works on `dorfquartier.net`.

## Notes

- The Strato builder scripts, tracking pixel, and server-side editor dependencies were not preserved because GitHub Pages is static-only.
- The original site does not appear to use a public contact form; this rebuild uses phone, mail, and map links.
- The Google map is embedded as a static iframe and may require accepting Google cookies depending on visitor settings.

## Visual refinement

The static rebuild was refined to sit closer to the original Strato design: darker brown header bar, right-aligned uppercase navigation with sand active states, a shorter image keyvisual with a centered brown title block, tighter white content panels, serif brown section headings, slimmer price rows, and simpler image/card styling. Exact parity is still limited by the original builder CSS/scripts and proprietary responsive behavior that are not included in this GitHub Pages version.

## Asset update

- The static site now includes the live Dorfquartier logo at `assets/images/dorfquartier-logo.png` and uses it in the header and hero area.
- The live favicon set was copied into `assets/icons/`, with `favicon.ico` generated for broad browser support. All top-level pages reference these with relative paths for GitHub Pages.
- The live Münsterland landscape is used as the page background via `assets/images/muensterland-background.jpg`.
- The Münsterland/Rheine content photo is included inline in the “Über das Münsterland & Rheine!” section as `assets/images/dorfquartier-muensterland.jpg`, not as a page background.
- The top hero/banner is transparent so it blends into the same page background and no longer shows the Münsterland/Rheine inline photo or another separate image behind the logo block.
