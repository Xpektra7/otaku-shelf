# Technical Requirements

### Frontend Stack
- React
- TanStack Query (data fetching/caching)
- React Router (routing)

### Backend Stack
- Node.js + Express
- Database: **your choice** (PostgreSQL recommended, MongoDB works too)
- Auth: JWT or sessions - **your choice**



## API Endpoints Needed

### Auth
```
POST   /api/auth/register          # Create account
POST   /api/auth/login             # Login
POST   /api/auth/logout            # Logout
GET    /api/auth/me                # Get current user info
```

### Anime (proxy to external API)
```
GET    /api/anime/search?q={query} # Search anime
GET    /api/anime/:id              # Get single anime details
```

### User Lists
```
GET    /api/lists                  # Get current user's lists
POST   /api/lists                  # Add anime to a list
                                   # Body: { animeId, listType, rating? }
PUT    /api/lists/:id              # Update list entry (move/rate)
DELETE /api/lists/:id              # Remove from list
```

### Social
```
GET    /api/friends                # Get user's friends list
POST   /api/friends                # Add friend by username
DELETE /api/friends/:userId        # Remove friend
GET    /api/activity               # Get friends' recent activity
```

### Profile
```
GET    /api/users/:username        # Get user profile + lists
```



## Database Schema (Suggested)

### Users
```
id (PK)
username (unique)
email (unique)
password_hash
created_at
```

### Lists
```
id (PK)
user_id (FK -> Users)
anime_id (from external API)
anime_title (cached)
anime_image (cached)
list_type (enum: 'watching', 'completed', 'plan_to_watch')
rating (1-10, nullable)
created_at
updated_at
```

### Friendships
```
id (PK)
user_id (FK -> Users)
friend_id (FK -> Users)
created_at
```

### Activity Feed (optional - can be generated on-the-fly)
```
id (PK)
user_id (FK -> Users)
action_type (enum: 'added', 'completed', 'rated')
anime_id
anime_title (cached)
rating (nullable)
created_at
```


## Frontend-Backend Contract

### Response Formats

**Success:**
```json
{
  "success": true,
  "data": { ... }
}
```

**Error:**
```json
{
  "success": false,
  "error": "Error message here"
}
```

### Auth Flow
1. Frontend sends credentials to `/api/auth/login`
2. Backend returns JWT token (or sets session cookie)
3. Frontend stores token in memory/localStorage
4. Frontend includes token in subsequent requests via `Authorization: Bearer {token}`



## Priority Build Order

**Phase 1 (Core):**
1. Auth system (register/login)
2. Anime search
3. Personal lists CRUD

**Phase 2 (Social):**
4. Friend system
5. Activity feed



## Open Questions for Backend
- [ ] Which anime API? (Jikan vs AniList - check rate limits/docs)
- [ ] Auth method? (JWT vs sessions, OAuth vs email/password)
- [ ] Database choice? (Postgres vs MongoDB)
- [ ] How to cache anime data? (To avoid hitting external API repeatedly)
- [ ] Rate limiting needed?



## Success Criteria
- 3-5 friends actively using it to track anime
- Core features work smoothly
- Good practice for TanStack Query + Node backend patterns
```

