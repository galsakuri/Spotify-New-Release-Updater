# Spotify-New-Release-Updater

## Features

Automatically keeps a Spotify playlist up to date with the latest releases from the artists you follow.

-	Authenticates with Spotify using OAuth (scopes: read & modify playlists, read follows).
-	Fetches the full list of artists you follow.
-	Retrieves all albums/singles from those artists.
-	Filters to only those released in the past 7 days, excluding remixes, instrumentals, live versions, etc (you can edit to your own liking).
-	De-duplicates by track URI, keeping only the most recent release per track.
-	Sorts the new tracks by release date (newest first).
-	Finds or creates a playlist (default “New Releases”) in your account.
-	Removes any tracks in that playlist older than 14 days.
-	Adds the freshly discovered tracks to the top of the playlist so the newest always appear first.

---

## Prerequisites

- **Python 3.8+**  
- **pip** (Python package installer)  
- A **Spotify Developer** account  

---

## Register Your Spotify App

1. Go to the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/).  
2. Click **“Create an App”**, give it a name/description.  
3. In your new app’s settings, add a **Redirect URI** (e.g. `http://localhost:8888/callback`).  
4. Copy your **Client ID** and **Client Secret** for the next step.

---

## Clone & Install

## Clone this repository
```bash
git clone https://github.com/your-username/spotify-new-release-updater.git
cd spotify-new-release-updater
```

---

## Configure Environment Variables

Create a file named `.env` in the project root with:

```dotenv
SPOTIPY_CLIENT_ID=<your_spotify_app_client_id>
SPOTIPY_CLIENT_SECRET=<your_spotify_app_client_secret>
SPOTIPY_REDIRECT_URI=<your_app_redirect_uri>
```

---

## Usage

```bash
python main.py [--playlist-name PLAYLIST] [--cache-path CACHE_FILE]
```

* `--playlist-name`
  Name of the playlist to create or update.
  **Default:** `New Releases`

* `--cache-path`
  Path to the token cache file where Spotify’s OAuth tokens are stored.
  **Default:** `token.json`

### Examples

1. **Default run**

   ```bash
   python main.py
   ```

2. **Custom playlist name**

   ```bash
   python main.py --playlist-name "My Favorites"
   ```

3. **Custom cache location**

   ```bash
   python main.py --cache-path ~/.spotify_token.json
   ```

On first run you’ll be prompted to log in to Spotify and grant permissions. After that, your tokens are cached so subsequent runs are non-interactive.

---

## Scheduling (Optional)

To run daily at 6 AM, you can use **cron** (Linux/macOS) or **Task Scheduler** (Windows).

### Cron example

```cron
0 6 * * * cd /path/to/spotify-new-release-updater && /usr/bin/python3 main.py --playlist-name "New Releases" --cache-path token.json >> updater.log 2>&1
```

### Windows Task Scheduler

1. Open Task Scheduler → Create Task.
2. Trigger: Daily at 6:00 AM.
3. Action:

   * Program/script: `python`
   * Add arguments: `C:\path\to\main.py --playlist-name "New Releases"`
   * Start in: `C:\path\to\spotify-new-release-updater`

---

## License

This project is licensed under the [MIT License](LICENSE).

```

Feel free to tweak any paths or names to fit your setup. Let me know if you need anything else!
```
