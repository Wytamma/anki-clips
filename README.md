# Anki Clips

Single-page JavaScript app to generate Anki flashcards from video clips.

## What it does

- Accepts one source video via drag-and-drop or file picker.
- Lets you add clips in a synced editor while watching the video.
- Supports optional question and answer text per clip.
- Clips each range in-browser using FFmpeg WebAssembly.
- Builds an Anki import ZIP containing:
	- `notes.tsv` (front/back fields)
	- `media/*.mp4` clips
	- `README_IMPORT.txt` with import steps

## Clip editor workflow

1. Drop a video file onto the upload area (or click to choose one).
2. Play/scrub the video.
3. Click **Mark start** and **Mark end**.
4. Optionally enter **Question text** and/or **Answer text**.
5. Click **Add clip**.
6. Edit clip cards (start/end/text) and use quick actions like **Go start**, **Start=Now**, **Delete**.

Time values can be either:

- seconds (example: `12.5`)
- `mm:ss`
- `hh:mm:ss` or `hh:mm:ss.ms`

Card side logic:

- If Question text exists: Front = question text, Back = answer text + video.
- If only Answer text exists: Front = video, Back = answer text.

## Run

```bash
npm install
npm run dev
```

Then open the local URL from Vite in your browser.

## Import into Anki

1. Unzip the generated `*_anki_import.zip` file.
2. Copy `media/*.mp4` into your Anki `collection.media` folder.
3. In Anki: File → Import → select `notes.tsv`.
4. Map field 1 to Front and field 2 to Back.
5. Video placement follows the question/answer rule above.

## Build

```bash
npm run build
npm run preview
```
