# Playlist API

A RESTful API for managing music playlists, built with Flask and PostgreSQL. Supports paginated song listing, full-text search, and rating updates.

## Tech Stack

- **Backend:** Flask, SQLAlchemy, PostgreSQL
- **Testing:** pytest with separate test database
- **Architecture:** App factory pattern, Blueprint-based routing, service layer

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/songs?page=1&per_page=10` | Paginated song listing |
| `GET` | `/search?search=<term>` | Case-insensitive title search |
| `PUT` | `/update_rating/<song_id>` | Update a song's rating |

## Getting Started

### Prerequisites

- Python 3
- PostgreSQL

### Setup

```bash
git clone https://github.com/prakhar450/playlist-api.git
cd playlist-api
pip install -r requirements.txt
```

Create two PostgreSQL databases:

```sql
CREATE DATABASE flask_db;
CREATE DATABASE test_db;
```

Set environment variables `DB_USERNAME` and `DB_PASSWORD`, or edit `playlist/config.py` directly.

Seed the database with sample data:

```bash
python scripts/initialize_database.py
```

### Run

```bash
python run.py
```

### Test

```bash
python -m pytest
```

## Project Structure

```
playlist/
  __init__.py          # App factory
  config.py            # Database configuration
  models.py            # Song model with JSONB support
  main/
    routes.py          # API endpoints
    services.py        # Business logic
  tests/
    conftest.py        # Test fixtures
    test_routes.py     # Route tests
    test_services.py   # Service tests
scripts/
  initialize_database.py  # Data seeding
data/
  playlist[76].json       # Sample playlist data
```

## Screenshots

**Get All Songs**
![Get All Songs](https://github.com/prakhar450/playlist-api/assets/55326021/21b99b66-72b0-4e8d-8a5e-55d8b3514107)

**Search for Song**
![Search for Song](https://github.com/prakhar450/playlist-api/assets/55326021/0620f4c2-d832-4c14-85ad-c8299571436e)

**Update Rating**
<img width="1787" alt="Update Rating" src="https://github.com/prakhar450/playlist-api/assets/55326021/f5e0efd7-660e-4609-8e6a-428a361c7139">
