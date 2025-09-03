# Flask + Redis with Docker Compose (Hands-on)

**Course:** Cloud Computing for Data Analysis — ITCS 6190/8190 (Fall 2025)  
**Instructor:** Marco Vieira  
**Student:** Swetha Pavuluri

---

## 1. PostgreSQL Setup

```bash
# Pull the PostgreSQL image
docker pull postgres

# Run a PostgreSQL container
docker run -d -p 5432:5432 --name postgres1 -e POSTGRES_PASSWORD=pass12345 postgres

# Open a shell in the container
docker exec -it postgres1 bash

# Launch the PostgreSQL client
psql -U postgres

## 2. Flask + Redis App Setup
a. Create the following files:

app.py

requirements.txt

Dockerfile

compose.yaml

b. Build and run the app with Docker Compose:
docker compose up --build

c. Access the app:

Visit: http://localhost:8000

Refresh the page multiple times—the counter should increment.

## 3. Screenshots to Include

Docker Desktop showing containers (postgres1, web, redis).

Logs from the web container showing Flask startup.

Browser output displaying:

Hello World! I have been seen N times.

## 4. Errors Encountered (Also Logged in GitHub Issues)
Error	Cause	Resolution
redis.exceptions.ConnectionError	Redis container not ready on launch	Added retry logic in app.py and waited a few seconds
psql: command not found inside container	Minimal Postgres image lacks client tools	Installed with:
apt-get update && apt-get install -y postgresql-client
``` |
| Port 8000 in use | Conflict with other local process | Changed mapping in `compose.yaml` to e.g. `8080:5000` |

---

## 5. What I Learned

- Running PostgreSQL and Redis in Docker containers.  
- How to access containers (`docker exec -it ...`).  
- Building a Flask app container with a `Dockerfile`.  
- Using Docker Compose to orchestrate multiple services.  
- Inter-container networking using service names.  
- Troubleshooting via logs and error messages.  
- Documenting setup steps and resolving issues clearly in GitHub.

---

## 6. Submission Checklist

- [ ] Uploaded files: `app.py`, `Dockerfile`, `compose.yaml`, `requirements.txt`, `README.md`
- [ ] Added screenshots (in a separate document or as `images/` folder)
- [ ] Logged all errors with descriptions and fixes under GitHub **Issues**
- [ ] Submitted the GitHub repo link on Canvas
