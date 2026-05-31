# Noah's Ark

An 8-bit Bible story adventure game about Noah.

## New Chat Handoff

Use this section first when picking up the game in a new chat.

- Folder: `/Users/aaronchu/noahs_ark`
- Open the game locally with `Click_This_To_Open_The_Game.html`. No dev server or internet access is required.
- On another computer, unzip the folder first, then double-click `Click_This_To_Open_The_Game.html` or open it with Chrome, Edge, Firefox, or Safari.
- Main files: `Click_This_To_Open_The_Game.html`, `styles.css`, `script.js`, `README.md`. The clickable HTML file is self-contained for easier Windows sharing; `styles.css` and `script.js` are kept as development source files.
- This is not currently a git repository.
- The game uses one canvas plus HTML menu/dialog overlays.
- Saves are stored in browser `localStorage` under four save slots.

Current playable flow:

1. Start a new game from the title screen.
2. As Noah, talk to the four corrupted townspeople in map 1.
3. Return to Noah's home. The God-calls-Noah cutscene begins.
4. The cutscene explains the Genesis 6 ark command and shows God as an ambiguous holy light.
5. After the cutscene, Noah is moved to the Phase 2 ark worksite.
6. The worksite connects to the gopher wood grove, pitch pits, and food store tents.
7. Gather required materials through minigames: wood, pitch, and food.
8. Return to the marked worksite and assemble the first ark frame by dragging timber pieces into place.
9. Return to the worksite and create rooms inside the ark with a deck-and-bay planning minigame.
10. Sort clean and unclean animal pairs into the rooms that were made.
11. Coat the ark with prepared pitch.
12. Load final food, feed, seed, and water stores into the prepared rooms.
13. Enter the ark. The current last scene is Noah's family embarking as the journey begins.

Recent implementation details:

- Dialogue always shows `Continue: Space / Enter`.
- Phase 2 map travel explains edge-path transitions once instead of interrupting on every area change.
- The Phase 2 Bible label is `Genesis 6:14-22 - Preparing the Ark`.
- The ark worksite begins as stakes and measuring cords; the visible ark frame appears only after the assembly minigame is completed.
- Food-packing orders are randomized each time the food minigame starts.
- The pitch minigame now forces low heat to recover upward so the meter cannot get stuck too cold.
- The pitch minigame now has a batch danger meter; staying outside the gold safe band too long resets the batch.
- Ark assembly pieces are intended to be 1:1 with their target outlines.
- Ark assembly drag-and-drop supports mouse, touch, and pen pointer input.
- After the frame, the worksite starts a rooms minigame using lower/middle/upper deck room planning rather than another drag puzzle.
- After rooms are complete, the worksite starts an animal sorting minigame using clean and unclean categories from Genesis 7.
- Rooms plans and animal cards are randomized each time their minigames start.
- After animal sorting, the worksite starts a pitch coating minigame where the player brushes pitch across the ark.
- After sealing, the worksite starts a final stores minigame with randomized supply order and room positions.
- The current story endpoint is the embark scene: the ark is sealed, stores are loaded, and Noah's family enters to begin the journey.
- Touch-capable browsers show an on-screen D-pad with a center interact button.
- The pitch minigame is a simplified pitch-preparation challenge.
- Audio is planned but not implemented.

Best next tasks:

- Do a real browser playthrough from a fresh save and from an older save.
- Add audio file support using an `assets/audio/` folder.
- Continue after the embark scene with rain, flood, waiting, raven/dove scouting, and the ending scenes.

Last known verification:

- `node --check script.js` passed after the embark-scene update.
- The embedded script inside `Click_This_To_Open_The_Game.html` was extracted and syntax-checked.
- The clickable HTML now bundles local CSS and JavaScript for Windows/Edge sharing.
- The clickable HTML was checked for external script/style/asset references; none are required to run the game.
- The code uses standard browser APIs supported by current Chrome, Edge, and Firefox. Touch controls include a fallback for older `matchMedia` listener behavior.
- Pitch completion was runtime-tested in a mocked browser canvas after fixing the post-completion `activeMinigame` null-state crash.
- All current minigame draw paths were runtime-tested in a mocked browser canvas: wood, pitch, food, ark frame, rooms, animals, sealing, final stores, and embark.
- Phase 2 maps were checked to render as `28x18`.
- Startup, rooms, animal sorting, sealing, final stores, and embark paths still need a full real-browser playthrough.
- Major fixed UI rectangles were checked for overlap.

## Current Status

Phase 2 has started with the ark-call cutscene, expandable worksite maps, material collection, ark-frame assembly, rooms-inside-the-ark planning, clean/unclean animal sorting, pitch sealing, final stores loading, and the embark scene.

The game currently covers the Genesis 6 opening and the ark preparation story beats: after Noah has heard all four corrupted townspeople and returns home, God calls Noah to build the ark. Noah then moves to an ark worksite, gathers early supplies, assembles the first ark frame, creates rooms inside, sorts a small set of clean and unclean animal pairs, seals the ark, loads final stores, and enters the ark to begin the journey.

## Audience

The game should stay clear, readable, age-appropriate, and easy to play without long instructions.

## Style Direction

- 8-bit / pixel-art presentation
- Top-down exploration inspired by classic Pokemon-era games
- Browser-based structure inspired by classic retro adventure games
- Biblical ancient-world setting instead of modern or fantasy visuals
- Dialogue boxes, simple quest prompts, menu overlays, and local save slots
- Short future minigames that keep the story moving

Noah's Ark should keep a retro adventure feel with clear pacing, menus, and interaction style.

## Phase 1 - Genesis 6: The Wicked World

Current implementation:

- `Click_This_To_Open_The_Game.html` defines the playable game. It includes bundled CSS and JavaScript so Microsoft Edge can open one file directly.
- Noah is the starting playable character.
- The title screen displays `Genesis 6-9` and the subtitle `The story of a righteous man.`
- The current in-game Bible reference is state-driven and currently shows `Genesis 6`.
- The main menu includes `New Game`, `Load Game`, and `About`.
- The About screen summarizes the story through the embark scene.
- The title menu uses Bible-story themed pixel art rather than showing the map behind it.
- The starting quest asks Noah to talk to townspeople and observe the wickedness around him.
- Townspeople dialogue shows mockery, violence, dishonesty, pride, and confusion in age-appropriate language.
- Noah's family dialogue is intentionally ambiguous rather than strongly claiming they are righteous.
- After hearing from the townspeople, Noah can return home to complete the current Phase 1 quest.

## Phase 2 - God Calls Noah

Current implementation:

- The Phase 2 cutscene begins only after the four corrupted townspeople have been heard and Noah returns to his home.
- God is represented visually as an ambiguous holy light, not as a person.
- The cutscene uses interactive dialogue advanced with `Space` or `Enter`, giving players control over reading pace.
- Every dialogue box shows a clear `Continue: Space / Enter` prompt.
- The dialogue explains the ark command clearly, including gopher wood, rooms, pitch inside and outside, three decks, a side door, a top opening/window, the biblical dimensions, food stores, the covenant promise, and God bringing living creatures to Noah.
- The cutscene state is saved so the ark call is not repeated after completion.
- After the cutscene, Noah moves to an expandable Phase 2 worksite map outside the settlement.
- The worksite begins as marked ground with stakes and measuring cords. The ark frame appears only after the assembly minigame is completed.
- The worksite connects to separate areas for a gopher wood grove, pitch pits, and food store tents.
- Phase 2 is labeled as `Genesis 6:14-22 - Preparing the Ark`, matching the biblical command and Noah's obedience in Genesis 6.
- Materials are collected through minigames: timed wood chopping, pitch preparation, and food packing.
- Each minigame opens with a directions box and a start button before play begins.
- After enough wood, pitch, and food are gathered, Noah can start a drag-and-place ark frame building minigame at the worksite.

## Current Map

The map represents an ancient settlement before the ark command. It includes:

- Noah's home
- market stall
- tent area
- public court
- well
- altar
- fenced animal pen
- paths, trees, fields, and water
- smaller in-world wooden signs near landmarks
- a working minimap in the top-right of the game view

Before the Phase 2 cutscene, the map intentionally does not include:

- ark frame
- ark materials
- wood piles for ark construction
- pitch, tools, or building preparation
- dialogue where family members already know about the ark

## Saves

Saves use browser `localStorage`.

This means saves should still be there after closing and reopening the page later in the same browser, unless that browser clears or blocks local storage. Saves are local to that browser and computer.

Current save behavior:

- Four save slots are available.
- `New Game` asks for a save name.
- A new game uses the first empty slot when one is available.
- If all four slots are full, the game opens an in-game slot picker and asks which slot should be overwritten.
- During gameplay, `Escape` or the top `Menu` button opens the pause menu.
- `Save Progress` opens a four-slot save menu.
- Any slot can be selected when saving.
- Occupied slots are overwritten directly when chosen from the save menu.
- The load menu shows all four slots.
- Occupied save slots include attached `Name` and `Delete` controls.
- Empty save slots do not show rename or delete controls.
- Save naming, renaming, overwrite selection, and delete confirmation use in-game modal windows instead of browser popups.
- New saves store stable ISO timestamps and display them in a readable format.
- Save loading validates progress and keeps older saves usable if future map changes make the old player position invalid.
- Save writing handles blocked browser storage without crashing the game.
- Saves track whether the ark-call cutscene has been completed.
- Saves track the current Phase 2 map, material counts, first ark frame, rooms, animal sorting, pitch sealing, final stores, and embark progress flags.

## Controls

- Move: `WASD` or arrow keys
- Touch movement: on-screen D-pad appears on touch-capable devices
- Interact / continue dialogue: `Space` or `Enter`
- Touch interact: center `OK` button on the D-pad
- Open pause menu: `Escape` or the top `Menu` button
- Menu confirm: `Enter` or `Space`
- Minigame start: click `START TASK` or press `Space` / `Enter`
- Wood minigame: press `Space` or `Enter` only when the marker reaches the gold cut zone
- Pitch minigame: keep heat in the gold safe band; too much time outside resets the batch
- Food minigame: click the matching supply crate
- Ark assembly minigame: drag timber pieces with mouse, touch, or pen
- Rooms minigame: click the room space matching the deck and bay plan
- Animal sorting minigame: click the clean or unclean room for each animal pair
- Seal minigame: hold and drag the pitch brush to coat the ark
- Final stores minigame: click the room that matches the current supply card

## Phase 2 Plan

Phase 2 has begun after the current Genesis 6 introduction.

Remaining planned scope:

- add rain, flood, waiting, dove/raven scouting, and ending scenes

## Audio Plan

Planned audio direction:

- Use real audio files rather than generating all sounds in code.
- Add an `assets/audio/` folder for music loops and sound effects.
- Prefer browser-friendly formats such as `.mp3` with optional `.ogg` fallbacks if needed.
- Keep all audio local so the game still works offline and on Windows after unzipping the game folder.
- Start audio only after the player clicks or presses a key, because browsers usually block autoplay before user interaction.

Planned music:

- title/menu loop
- quiet settlement exploration loop
- gentle holy-light ambience for the God-calls-Noah cutscene
- ark worksite loop
- short task/minigame loop or rhythm bed

Planned sound effects:

- menu move / menu confirm
- dialogue advance or soft dialogue blip
- save success
- map transition
- wood chop hit and miss
- pitch stir / pitch ready
- food crate pack / wrong crate
- ark timber pickup, drag, snap, and task complete

Audio should stay calm, readable, not startling, and easy to mute later if an options menu is expanded.

## Known Issues / Next Review

No blocking syntax or startup errors were found in the final check, but these areas should be reviewed next:

- Full browser playtesting is still needed from a fresh save and from an older saved game. Current automated checks use Node and a mocked browser canvas, not a real browser automation suite.
- Touchscreen support for ark assembly now uses pointer events, but it still needs a physical tablet or touchscreen laptop check.
- The food-packing order is randomized and not stored mid-minigame; leaving or refreshing during that task restarts the task order.
- Minigame progress is saved only after a task completes, not while the task is in progress.
- Some canvas text uses fixed `fillText` positions instead of automatic wrapping, so very small browser windows or unusual font rendering should be checked manually.
- The Phase 2 pitch task is a simplified pitch-preparation challenge.
- Audio is planned but not implemented yet.

## Later Phase Ideas

Possible later phases:

- weather or flood survival minigames
- waiting inside the ark
- raven and dove scouting scenes
- end with dry land and a peaceful closing sequence

Possible minigames:

- rain leak repair reaction game
- storm balance game while the ark rocks
- dove scouting sequence near the ending

## Local Sharing

Because this is a static browser game, other people should be able to play it locally by receiving the full game folder and opening `Click_This_To_Open_The_Game.html` in a browser.

For sharing from Mac to Windows:

1. Make sure the folder includes `Click_This_To_Open_The_Game.html`. Keep `styles.css`, `script.js`, images, sounds, and this `README.md` too if you want the editable files.
2. Compress the complete `noahs_ark` folder into a `.zip` file.
3. Send the `.zip` file to the target computer.
4. On Windows, unzip/extract the folder first. Do not open the HTML file from inside the compressed `.zip` window.
5. Open `Click_This_To_Open_The_Game.html` in a current version of Chrome, Edge, or Firefox. Internet Explorer is not supported.

Do not send only the Downloads folder unless it contains the complete game folder with every file the game needs. The safest option is one zipped game folder.

If Microsoft Edge shows a red `Game error` message, copy that exact message for debugging. If the page looks like plain text, the file may have been opened in a text editor instead of a browser.

Before sharing, test the final package on a Windows computer and confirm:

- the game opens by double-clicking `Click_This_To_Open_The_Game.html`
- all images and sounds load correctly
- keyboard controls work
- saves behave as expected
- the game does not require internet access

## Files

- `Click_This_To_Open_The_Game.html` - self-contained game file to double-click and play
- `styles.css` - editable source for page layout, menu styling, save slot UI, and responsive presentation
- `script.js` - editable source for game state, map drawing, dialogue, input, save slots, and quest logic
- `README.md` - notes and implementation status
