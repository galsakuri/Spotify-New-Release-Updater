# Spotify Weekly New Release Auto-Updater

Automatically keeps a Spotify playlist up to date with the latest releases from the artists you follow.

---

## Table of Contents

1. [Prerequisites](#prerequisites)  
2. [Register Your Spotify App](#register-your-spotify-app)  
3. [Clone & Install](#clone--install)  
4. [Configure Environment Variables](#configure-environment-variables)  
5. [Usage](#usage)  
6. [Scheduling (Optional)](#scheduling-optional)  
7. [Troubleshooting](#troubleshooting)  
8. [Contributing](#contributing)  
9. [License](#license)  

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

```bash
# Clone this repository
git clone https://github.com/your-username/spotify-new-release-updater.git
cd spotify-new-release-updater

# (Optional) Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate    # macOS/Linux
.\.venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt