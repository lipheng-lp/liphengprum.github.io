# liphengprum.github.io

Personal academic site. Plain HTML/CSS, no build step, no dependencies.

```
index.html   all page content
style.css    all styling (light + dark; tokens at the top of the file)
assets/      photo and videos
.nojekyll    tells GitHub Pages to serve files as-is
```

Preview by opening `index.html` in a browser.

## Videos

The five thesis and automation clips were 1080p phone recordings totalling 156 MB.
They are re-encoded here to 720p H.264 (CRF 26, audio stripped, `+faststart`) which
brings them to about 22 MB with no visible loss at page size. The originals are
untouched in the parent folder. Re-encode from those if you ever need better quality:

```
ffmpeg -i INPUT.mp4 -vf "scale='min(1280,iw)':-2" -c:v libx264 -crf 26 \
       -preset slow -pix_fmt yuv420p -movflags +faststart -an OUTPUT.mp4
```

`Supplementary.mp4` and `Locomotion.mp4` are the research renders, copied as-is.

## Deploy

The repo is initialized and committed locally, with `user.name` and `user.email` set
per-repo so commits are not attributed to this machine's global `camtechailab` identity.

1. On github.com create a **public** repo named exactly `liphengprum.github.io`.
   Leave it empty, with no README, no license and no .gitignore.
2. Then:

   ```
   git remote add origin https://github.com/lipheng-lp/liphengprum.github.io.git
   git push -u origin main
   ```

3. In the repo, go to Settings, then Pages. Set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Live at <https://lipheng-lp.github.io/liphengprum.github.io/> within a couple of minutes.

Every later `git push` redeploys automatically.

## Editing

- **A publication.** Copy an `<li>` block inside `<ol class="pubs">`.
- **A job or degree.** Copy an `<li>` block inside the relevant `<ol class="timeline">`.
- **A video.** Copy a `<figure>` block inside a `<div class="media">`.
- **Colours.** The `:root` block at the top of `style.css`. The page is light only,
  so each token is defined once and every change takes effect everywhere.
