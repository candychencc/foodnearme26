# My 2KM Food Directory

A single-page, self-contained food directory for places near 26 Pasir Ris Link, Singapore.
Pure HTML/CSS/JS — no build step, no dependencies, no backend.

## Deploy on Vercel via GitHub

1. **Create a GitHub repo**
   - Go to github.com → New repository (e.g. `food-directory`).
   - Upload the contents of this folder (`index.html`, `vercel.json`) to the repo —
     either via the GitHub web UI ("Add file → Upload files") or:
     ```bash
     git init
     git add .
     git commit -m "Initial commit"
     git branch -M main
     git remote add origin https://github.com/<your-username>/food-directory.git
     git push -u origin main
     ```

2. **Import into Vercel**
   - Go to vercel.com → Add New → Project.
   - Choose "Import Git Repository" and select the repo you just pushed.
   - Framework Preset: choose **Other** (or leave as detected — it's a static site,
     no build command or output directory is needed).
   - Click **Deploy**.

3. **Done** — Vercel will give you a live URL (e.g. `food-directory.vercel.app`).
   Any future push to the `main` branch will auto-redeploy.

## Editing the data

Open `index.html` and find the `restaurants` array inside the `<script>` tag near
the bottom of the file. Each entry follows this shape:

```js
{
  name, category, cuisine, address, latitude, longitude,
  budget, rating, ratingCount, ratingSource, description, image,
  googleMapsPlaceId, grabFoodUrl, foodpandaUrl, openingHours
}
```

- `grabFoodUrl` / `foodpandaUrl` are `null` by default — set them to a real URL
  string to activate those buttons on a card.
- Distances are calculated automatically from the `HOME` coordinates at the top
  of the script (currently set to 26 Pasir Ris Link).
- To connect a real interactive map, replace the `.map-placeholder` block in the
  HTML with an embedded Google Maps / Maps JavaScript API element, reusing the
  same `HOME` coordinates.
