# Lumi

Lumi is a soft, playful journal and task space for daily planning, reflection, and wellbeing.

It combines:
- a calendar-first daily view
- a task drawer for storing all tasks and assigning them to dates
- a Daily Canvas for notes, mood, and stickers
- per-task progress tracking for goal-based tasks
- private user accounts with Supabase
- a mobile-friendly PWA experience

## Features

- Private sign up and sign in
- Preferred name greeting
- Monthly calendar with assigned tasks and sticker mood previews
- Daily notes with rich text, links, and rotating prompts
- Task categories with icons and colors
- Drag-and-drop on desktop and touch-friendly mobile behavior
- Progress tracking for tasks with target dates
- Installable mobile web app with home screen icon support

## Tech Stack

- HTML
- CSS
- Vanilla JavaScript
- Supabase Auth + Database
- Vercel for hosting

## Project Structure

- `index.html` - app layout and UI structure
- `styles.css` - visual design, layout, and responsive styling
- `script.js` - app logic, calendar, tasks, notes, auth, and persistence
- `manifest.json` - PWA metadata
- `sw.js` - service worker
- `app-config.js` - local Supabase config
- `app-config.example.js` - example config template
- `database.sql` - Supabase table and RLS policies
- `icons/` - app icons for favicon, Apple touch icon, and PWA install

## Local Setup

### 1. Clone or download the project

Put the project in a local folder and open it in your editor.

### 2. Create a Supabase project

- Create a new project in Supabase
- Copy your project URL
- Copy your anon public key

### 3. Create the database table

Open the Supabase SQL editor and run the SQL in `database.sql`.

This creates:
- `public.user_journal_state`
- row level security policies so each user only accesses their own data

### 4. Add your config

Copy `app-config.example.js` to `app-config.js` if needed, then fill in:

```js
window.APP_CONFIG = {
  supabaseUrl: "https://YOUR_PROJECT_ID.supabase.co",
  supabaseAnonKey: "YOUR_SUPABASE_ANON_KEY",
};
```

### 5. Enable email auth

In Supabase Auth:
- enable Email authentication
- optionally disable email confirmation while testing

### 6. Run the site

This is a static site, so there is no build step.

You can open it with a local web server, for example:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## Deployment

Lumi can be deployed as a static website on:
- Vercel
- Netlify
- GitHub Pages

Make sure these files are included:
- `index.html`
- `styles.css`
- `script.js`
- `manifest.json`
- `sw.js`
- `app-config.js`
- `icons/`

## Mobile Web App

Lumi supports installation as a PWA.

Users can:
- open the deployed website on mobile
- add it to the home screen
- launch it like an app

Typical install paths:
- iPhone Safari: Share -> Add to Home Screen
- Android Chrome: Install app / Add to Home Screen

## Data and Privacy

- Each signed-in user has a private journal state
- Data is stored in Supabase
- User data is not shared across accounts
- If Supabase is not configured, the app falls back to local browser storage

## Notes

- Existing users created before the preferred-name field may need to sign in once and enter their preferred name so it can be saved
- If PWA changes do not show on mobile immediately, remove the installed app and reinstall after redeploying

## License

Add your preferred license here.
