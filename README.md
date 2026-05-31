# Noah's Ark

A browser game about Noah's obedience in Genesis 6 and the preparation of the ark.

The game follows Noah through a corrupt settlement, the call from God, the gathering of supplies, the building of the ark frame, room planning, animal sorting, sealing the ark with pitch, loading final stores, and entering the ark as the journey begins.

## Play

Open the game in a browser:

- Local file: `Click_This_To_Open_The_Game.html`
- Web version: use `index.html` through GitHub Pages

For iPhone, use the GitHub Pages link in Safari. Opening the HTML file from the iOS Files app may use Apple's preview viewer instead of Safari, which can break buttons and touch controls.

## Controls

- Move: `WASD`, arrow keys, or the on-screen D-pad
- Interact / continue dialogue: `Space`, `Enter`, or the D-pad `OK` button
- Open menu: `Escape` or the home button in the top-left corner
- Touch screens: hold a D-pad direction to keep moving

Minigames use simple mouse, keyboard, or touch input depending on the task. Each minigame includes directions before it starts.

## Saves

Progress is saved in the player's browser using local storage.

Saves are private to each browser and device. They are not uploaded to GitHub and are not shared between players. Clearing browser data can remove saves.

## Files

- `index.html` - GitHub Pages entry point
- `Click_This_To_Open_The_Game.html` - self-contained local version
- `script.js` - game logic and canvas drawing
- `styles.css` - page, menu, dialogue, and touch-control styling
- `README.md` - project notes

The standalone HTML files include the CSS and JavaScript so the game can run from a single file when needed.

## Deploying

This project is set up for GitHub Pages using the workflow in `.github/workflows/pages.yml`.

To publish updates:

```bash
git add .
git commit -m "Update game"
git push
```

After pushing, GitHub Actions will rebuild the Pages site. The public game URL is:

```text
https://AaronChu-CS.github.io/noahs-ark-game/
```

Browsers may cache old files, so refresh the page if an update does not appear right away.

## Browser Support

The game is designed for current versions of:

- Safari on iPhone
- Chrome
- Edge
- Firefox

No server code is required. GitHub Pages only hosts the static files.
