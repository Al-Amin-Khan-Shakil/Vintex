markdown
# Ventix

A ticketing platform where organizers can create events, sell tickets, and verify attendees via QR code check-in at the door.

## Tech Stack

- Ruby 4.0.7 / Rails 8.1.3
- PostgreSQL 17
- Tailwind CSS (via `tailwindcss-rails`)
- Hotwire (Turbo + Stimulus)
- Docker Compose for local development

## Getting Started

This project runs entirely in Docker — you don't need Ruby, Rails, or Postgres installed on your machine, only Docker itself.

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) and Docker Compose installed and running
- Git

### Setup

1. Clone the repo:

git clone git@github.com:Al-Amin-Khan-Shakil/Vintex.git
cd Vintex


2. Build the containers:

docker compose build


3. Start the app:

docker compose up -d


4. Create and migrate the database (first time only):

docker compose exec web bin/rails db:create db:migrate


5. Visit **http://localhost:3000**

### Everyday commands

| Task                          | Command                                      |
|-------------------------------|-----------------------------------------------|
| Start the app                 | `docker compose up -d`                        |
| Stop the app                  | `docker compose down`                         |
| View logs                     | `docker compose logs -f web`                  |
| Run a Rails command           | `docker compose exec web bin/rails <command>` |
| Run tests                     | `docker compose exec web bin/rails test`      |
| Rails console                 | `docker compose exec web bin/rails console`   |
| Install a new gem             | Add to `Gemfile`, then `docker compose build` |

### Notes

- Port 5432 (Postgres) must be free on your host machine — if you have a local PostgreSQL install running, stop it first (`sudo systemctl stop postgresql` on Linux/WSL), or it'll conflict with the container.
- Database data persists in a Docker volume between restarts. To wipe it completely and start fresh: `docker compose down -v`.