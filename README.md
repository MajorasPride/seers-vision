# Seer’s Vision

v1.0, made by MajorasPride.

A phone-first web app that finds a Magic: The Gathering card in the camera, reads its name, finds the exact printing on Scryfall, and adds it to a collection list kept in the browser.

## Use it

Open the page over https (GitHub Pages works), allow the camera, and hold a card inside the frame. When the outline turns green the card is read. Check the printing, tap **Add to collection**, and scan the next one.

- **Auto-add** (on by default since v1.0.1) adds a card right away when both the name and the printing are sure; otherwise the confirm sheet opens with the reason (Not sure of the name, Check the printing, or Printings did not load).
- **Use a photo** scans a picture instead of the live camera.
- **Collection** has search, sorting, quantity and foil editing, price totals, and export and import as a plain text list (`1 Sol Ring (C21) 263`) or CSV.

The collection is saved in this browser on this device only.

## How it works

Everything is in `index.html`.

1. OpenCV.js finds the largest four-corner shape with a card's 63 by 88 ratio and flattens it.
2. Tesseract.js reads the name bar.
3. Scryfall matches the name (`/cards/named?fuzzy=`, then `/cards/autocomplete`).
4. The printing is picked from the set code and collector number printed at the bottom left when they can be read, otherwise by comparing the art box with each printing's art using a 64-bit difference hash.

Libraries load from cdn.jsdelivr.net at pinned versions: `@techstark/opencv-js@4.10.0-release.1`, `tesseract.js@5.1.1`, `tesseract.js-core@5.1.1`, `@tesseract.js-data/eng@1.0.0`.

## Publish on GitHub Pages

Put `index.html` at the root of the repository, then Settings, Pages, deploy from the `main` branch root.

Card data and images come from [Scryfall](https://scryfall.com). This project is not affiliated with Wizards of the Coast.
