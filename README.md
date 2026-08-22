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

## Before you publish

1. **Your CV carries three mobile numbers.** `assets/Lipheng_Prum_CV.pdf` is the full
   CV and is linked live from the header. Page 2 lists your own number
   (+855-69-496-175) and, under References, the personal mobiles and emails of
   Prof. John Morris (+66 086-224-9239) and Asst. Prof. Dr. May Thu (+855 15 559 050).
   Your own number is your call. Theirs is not: they did not agree to have it
   scraped off a public page. Recommended fix is to save a copy of the CV with the
   References section deleted, overwrite `assets/Lipheng_Prum_CV.pdf` with it, and
   keep the full version for applications only.

2. **The transcripts are deliberately not on the site.**
   `assets/degree-certificates.pdf` holds only the two certificates: the Chaiyaphum
   Rajabhat bachelor's and the KMITL master's. The transcript pages of the source PDF
   were left out because they carry your date of birth (29 January 1995) and Cambodian
   personal ID (KHL-P19950129). Name plus date of birth plus national ID on a public
   page is the standard identity-fraud bundle. Send the transcripts privately when an
   application asks for them.

3. **Check the manuscript and supplementary video before pushing.**
   `assets/precision-curricula-manuscript.pdf` shows no author names, which usually
   means an anonymized submission copy. If it is under review somewhere, confirm that
   posting it is allowed and that neither it nor `assets/Supplementary.mp4` carries a
   venue watermark or submission ID.

4. **DOI.** The CV lists `10.1109/ICSEC56337.2022`, which looks truncated. IEEE DOIs
   normally end in an article number. Confirm the link resolves and fix it if not.

## Deploy

The repo is initialized and committed locally, with `user.name` and `user.email` set
per-repo so commits are not attributed to this machine's global `camtechailab` identity.

1. On github.com create a **public** repo named exactly `liphengprum.github.io`.
   Leave it empty, with no README, no license and no .gitignore.
2. Then:

   ```
   git remote add origin https://github.com/liphengprum/liphengprum.github.io.git
   git push -u origin main
   ```

3. In the repo, go to Settings, then Pages. Set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Live at <https://liphengprum.github.io> within a couple of minutes.

Every later `git push` redeploys automatically.

## Editing

- **A publication.** Copy an `<li>` block inside `<ol class="pubs">`.
- **A job or degree.** Copy an `<li>` block inside the relevant `<ol class="timeline">`.
- **A video.** Copy a `<figure>` block inside a `<div class="media">`.
- **Colours.** The `:root` block at the top of `style.css`. The page is light only,
  so each token is defined once and every change takes effect everywhere.
