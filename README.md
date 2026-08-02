# Jeenamaa Birthday Site — fully static photo album

No server, no API, no database. Photos are just image files sitting in the
`photos/` folder, referenced directly with `<img src="photos/filename.jpg">`.
Whatever you upload to the folder before hosting is what every visitor sees,
on any device — because it's literally part of the site.

## How to add a photo

1. Drop the image file into the `photos/` folder (e.g. `photos/goa-trip.jpg`).
2. Open `index.html`, find this block near the bottom (search for
   `const photos = [`):

   ```js
   const photos = [
     { file: 'goa-trip.jpg', title: 'Our first trip to Goa', date: '2024-11-02', note: 'Sunset on the beach 🌅' },
   ];
   ```

3. Add one line per photo. Only `file` is required — `title`, `date`, and
   `note` are optional (use `''` to skip them).
4. Save and refresh the page (or redeploy, if it's already hosted).

That's the entire workflow — edit the array, drop in the file, done.

## Running it

Just double-click `index.html`. No install, no build step, no terminal —
it works straight from your file system since there's no `fetch()` or API
call involved anywhere.

## Hosting it so others can see it

Any static host works, since there's no backend to run:

- **GitHub Pages** — push this folder to a repo, enable Pages in settings.
- **Netlify / Vercel** — drag-and-drop the folder in their dashboard, or
  connect the repo. Zero config needed since it's plain HTML.
- Literally any web host, even a shared hosting plan — just upload the
  files.

## What I'd extend first

1. **Compress photos before adding them** — since these load directly with
   no server-side resizing, a few full-resolution phone photos (5–10MB
   each) will make the page slow to load. Running them through something
   like [Squoosh](https://squoosh.app) or `tinypng.com` down to ~200–400KB
   each keeps it fast.
2. **A tiny build script to auto-generate the array** — once you have a
   dozen+ photos, hand-typing entries gets tedious. A short Node script
   that reads the `photos/` folder and prints the array for you to paste
   in would save time (happy to write that if it'd help).
3. **If you ever want live uploads from any device** (not just editing this
   file yourself before hosting), that's the backend version from before —
   worth revisiting only if you actually need strangers/family to upload
   without your involvement.
