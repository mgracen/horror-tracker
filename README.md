# Horror Tracker

A personal horror and thriller movie tracker built as a free, self-hosted web app. Search any film, track what you've watched, log notes and ratings, and get curated recommendations sourced from r/horror, Bloody Disgusting, Fangoria and Fantasia.

Built by [Mike Gracen](https://github.com/mgracen).

---

## Features

- **Search and add any film** - IMDb score, Rotten Tomatoes score, synopsis and poster auto-load via OMDB
- **Track your list** - watched, currently watching, want to watch
- **Watch count** - track how many times you've seen each film
- **Last watched date** - log when you watched it
- **Personal notes and star rating** - your own private thoughts on each film
- **Deduplication** - adding a film you already have catches the duplicate instantly
- **Recommendations tab** - curated picks sourced from r/horror, Bloody Disgusting, Fangoria and Fantasia festival picks, matched to your taste. Approve to add to your list, reject to dismiss.
- **Upcoming releases tab** - confirmed upcoming horror releases with dates, synopsis and notable context
- **Dark mode** - automatic based on system preference
- **Free to use** - no accounts, no ads, no monetisation

---

## Stack

| Layer | Service | Cost |
|---|---|---|
| Frontend | GitHub Pages | Free |
| Backend | Railway | Free tier |
| Scores and data | OMDB API | Free (1,000 req/day) |
| Data storage | Browser local storage | Free |

---

## Setup

### 1. Get a free OMDB API key

Go to [omdbapi.com/apikey.aspx](https://www.omdbapi.com/apikey.aspx), select Free, sign up and activate via the email they send you.

### 2. Deploy the backend to Railway

- Create a free account at [railway.app](https://railway.app)
- Connect your GitHub account
- Create a new project, deploy from GitHub repo, select horror-tracker-backend
- Add environment variable: OMDB_KEY = your OMDB key
- Generate a domain in Settings under Networking

### 3. Configure and deploy the frontend

Edit index.html and fill in the two config lines at the top of the script:

const OMDB_KEY = 'your_omdb_key';
const BACKEND  = 'https://your-railway-url.up.railway.app';

- Push to GitHub
- Enable GitHub Pages: Settings, Pages, Deploy from branch, main
- Your app will be live at https://YOURUSERNAME.github.io/horror-tracker

### 4. Import your film list

- Open your site and press Ctrl + Shift + J to open the console
- Type allow pasting and hit Enter
- Paste the contents of import.js and hit Enter
- Refresh the page

### 5. Backfill posters and scores

- In the console, paste the contents of patch.js and hit Enter
- Wait about 30 seconds for all films to update
- Refresh the page

---

## Updating recommendations

Recs and upcoming releases are curated manually and updated periodically. To refresh:

1. Update CURATED_RECS and CURATED_UPCOMING in server.js
2. Push to GitHub and Railway redeploys automatically in about 30 seconds
3. Hit the refresh button on the Recs or Upcoming tab

---

## Files

horror-tracker/
└── index.html              the entire frontend app

horror-tracker-backend/
├── server.js               Express backend, serves recs and upcoming
├── package.json            dependencies
└── .nvmrc                  tells Railway to use Node 20

---

## Data privacy

Your film list, notes, ratings and watch dates are stored entirely in your browser's local storage. No data is sent to any server. The backend only serves recommendation and upcoming release data and never receives or stores anything about your personal list.

---

## License

Personal use. Do whatever you want with it.
