# Spotify Playlist Creator

A web app for creating Spotify playlists from complete artist discographies with smart deduplication.

## Features

- Create playlists from one or multiple artists
- Smart deduplication removes duplicate tracks across albums
- Keeps variations (live, acoustic, remix, etc.) separate from standard versions
- Fetches complete discography including albums, singles, and compilations

## Setup

### 1. Create a Spotify App

1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Create a new app
3. Add redirect URI: `http://127.0.0.1:8888/spotify-playlist-creator.html`
4. Note your Client ID and Client Secret

### 2. Configure Credentials

```bash
cp config.example.js config.js
```

Edit `config.js` and add your credentials:

```javascript
const SPOTIFY_CONFIG = {
    CLIENT_ID: 'your_client_id_here',
    CLIENT_SECRET: 'your_client_secret_here',
    REDIRECT_URI: 'http://127.0.0.1:8888/spotify-playlist-creator.html'
};
```

### 3. Run Local Server

```bash
python3 -m http.server 8888
```

### 4. Open in Browser

Navigate to: `http://127.0.0.1:8888/spotify-playlist-creator.html`

## Usage

1. Click "Login with Spotify" and authorize the app
2. Enter artist names (one per line or comma-separated):
   ```
   Andy Shauf
   Sufjan Stevens
   ```
   or:
   ```
   Andy Shauf, Sufjan Stevens
   ```
3. Enter a playlist name
4. Click "Create Playlist"

The app will search for each artist, fetch all their tracks, deduplicate them, and create a private playlist in your Spotify account.

## Notes

- `config.js` is gitignored to protect your credentials
- Playlists are created as private by default
- If an artist is not found, it will be skipped
