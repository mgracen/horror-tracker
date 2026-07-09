# Horror Tracker

A personal horror and thriller movie tracker. Search any film, track what you have watched, log notes and ratings, and get curated recommendations sourced from r/horror, Bloody Disgusting, Fangoria and Fantasia.

**Live app: [mgracen.github.io/horror-tracker](https://mgracen.github.io/horror-tracker)**

Built by [Mike Gracen](https://github.com/mgracen).

---

## Features

- Search and add any film - IMDb score, Rotten Tomatoes score, poster and synopsis auto-load
- Track your list - watched, want to watch
- Watch count - track how many times you have seen each film
- Last watched date - log when you watched it
- Personal notes and star rating - your own private thoughts per film
- Sort by - a to z, your rating, IMDb score, date watched, most viewed, date added
- Deduplication - adding a film you already have catches the duplicate instantly
- Recommendations tab - curated picks sourced from r/horror, Bloody Disgusting, Fangoria and Fantasia, matched to your taste. Approve to add to your list, reject to dismiss.
- Upcoming releases tab - confirmed upcoming horror releases with dates, synopsis and notable context
- Five colour themes - blood red, midnight, frankenstein green, deep purple, bone
- Export to CSV or PDF
- Dark by default - built for horror people

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

```javascript
const OMDB_KEY = 'your_omdb_key';
const BACKEND  = 'https://your-railway-url.up.railway.app';
```

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

## Refreshing posters

Amazon CDN poster URLs expire periodically. If posters disappear, open the console and paste patch.js again to refresh them all.

---

## Updating recommendations

Recs and upcoming releases are curated manually and updated periodically. To refresh:

1. Update CURATED_RECS and CURATED_UPCOMING in server.js
2. Push to GitHub and Railway redeploys automatically in about 30 seconds
3. Hit the refresh button on the Recs or Upcoming tab

---

## Files

```
horror-tracker/
├── index.html          the entire frontend app
├── import.js           one-time script to bulk import your film list
├── patch.js            script to backfill posters and scores
└── README.md           this file

horror-tracker-backend/
├── server.js           Express backend, serves recs and upcoming
├── package.json        dependencies
└── .nvmrc              tells Railway to use Node 20
```

---

## Data privacy

Your film list, notes, ratings and watch dates are stored entirely in your browser local storage. No data is sent to any server. The backend only serves recommendation and upcoming release data and never receives or stores anything about your personal list.

---

## License

Personal use. Do whatever you want with it.
