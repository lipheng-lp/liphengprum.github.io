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

Every document below is linked live from the page. Nothing is public until you push.

1. **The transcripts are now included, at your request.**
   `assets/degree-and-transcript.pdf` is the complete five-page file: both certificates
   and both transcripts. The transcript pages carry your date of birth (29 January 1995)
   and your Cambodian personal ID (KHL-P19950129). Name plus date of birth plus national
   ID on a scrapeable page is the combination used to open accounts in someone else's
   name. You decided to publish it and that is your call, but it is worth revisiting
   before the push. Swapping in a certificates-only version later is a one-file replace.

2. **Your CV carries three mobile numbers.** Page 2 lists your own (+855-69-496-175)
   and, under References, the personal mobiles and emails of Prof. John Morris
   (+66 086-224-9239) and Asst. Prof. Dr. May Thu (+855 15 559 050). Yours is your
   decision. Theirs is not: they did not agree to be reachable from a public page.
   Save a copy with the References section deleted over `assets/Lipheng_Prum_CV.pdf`
   and the link keeps working.

3. **What was trimmed from the thesis and the conference paper, and why.**
   `assets/thesis-label-attachment.pdf` is pages 1 to 43 of `Thesis Paper.pdf`, the
   thesis itself. Page 44 was left out because it is the author biography listing your
   permanent home address in Kratie, your date of birth, and an old phone number.
   Pages 45 to 59 are the signed KMITL certification form and a Turnitin report.
   `assets/icsec2022-paper.pdf` is pages 1 to 5 of `Conference Paper.pdf` for the same
   reason: pages 6 to 20 are a Turnitin report and a form carrying your signature and
   Asst. Prof. Dr. Rutchanee Gullayanon's. Say the word if you want either restored in
   full.

4. **Check the manuscript and supplementary video before pushing.**
   `assets/precision-curricula-manuscript.pdf` shows no author names, which usually
   means an anonymized submission copy. If it is under review, confirm that posting it
   is allowed and that neither it nor `assets/Supplementary.mp4` carries a venue
   watermark or submission ID.

5. **DOI.** Corrected to `10.1109/ICSEC56337.2022.10049335`, the full article DOI.

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
