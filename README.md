# Otaku Shelf ( dedicated to my waifus )

A minimal social anime tracking app (Letterboxd-style) for friends to track what they're watching and see each other's activity. 

## Target Users
Small friend groups who watch anime and want a simpler alternative to MyAnimeList.

## Core Features (MVP)

### 1. Authentication
- User registration (email + password OR OAuth - **decide together**)
- Login/logout
- Protected routes for authenticated users only

### 2. Anime Search & Browse
- Search anime by title
- Display results: title, cover image, year, synopsis
- **Data Source:** Jikan API (MyAnimeList) or AniList API - **backend decides**

### 3. Personal Lists
Each user can organize anime into 3 lists:
- **Watching** - currently watching
- **Completed** - finished watching
- **Plan to Watch** - want to watch later

**List Actions:**
- Add anime to a list
- Move anime between lists
- Remove anime from lists
- Rate anime (1-10 scale) when marked as completed

### 4. User Profile
- View own profile with all lists
- Display username
- Show total anime counts per list

### 5. Social Features (Minimal)
- Add friends by username
- View friends list
- See friends' recent activity feed:
  - "[Friend] completed [Anime Title] - rated 8/10"
  - "[Friend] started watching [Anime Title]"
  - Last 10-20 activities, chronologically

## Out of Scope (Not in MVP)
- Reviews/comments
- Recommendations algorithm
- Episodes tracking
- Notifications
- Public profiles/discovery
- Advanced filtering/sorting
