# Docker Container Project

## Project Overview
This project demonstrates a containerized web application system using Docker and Docker Compose. It includes:

- A **Python Flask web application** container
- An **nginx container** serving static HTML content
- A **Redis container** for caching and state management

The project shows the ability to create Dockerfiles, set up multi-container orchestration, configure networking, and expose ports for accessing services.

## Folder Structure
```
leave_docker_project/
├─ webapp/                   # Flask app
│  ├─ app.py
│  ├─ requirements.txt
│  └─ Dockerfile
├─ static_site/              # nginx static site
│  ├─ index.html
│  └─ Dockerfile
├─ docker-compose.yml
├─ build.sh
└─ run.sh
```

## Services

1. **Flask Web App**
   - Runs on port **5000**
   - Connects to Redis for tracking visits

2. **nginx Static Site**
   - Runs on port **8080**
   - Serves static HTML content

3. **Redis Cache**
   - Runs on port **6379**
   - Provides caching for Flask app

## Setup Instructions

### Prerequisites
- Docker installed
- Docker Compose installed
- Internet connection (for pulling images)

### Build Containers
```bash
chmod +x build.sh
./build.sh
```

### Run Containers
```bash
chmod +x run.sh
./run.sh
```

### Handling Occupied Ports
If ports 5000, 8080, or 6379 are already in use, you can either:

1. **Kill the process using the port:**
```bash
# Example for port 5000
fuser -k 5000/tcp
```

2. **Change the port in docker-compose.yml:**
```yaml
ports:
  - "5001:5000"  # change host port 5000 to 5001
```
Replace 5001 with any free port.

### Access Services
- **Flask App:** [http://localhost:5000](http://localhost:5000) or updated port
- **Static Site:** [http://localhost:8080](http://localhost:8080) or updated port

## Notes
- Ensure ports are free or updated before running.
- Clean up containers after use with `docker-compose down`.
- This setup can be extended to include more services.

## Author
- Developed by Ajay Pawar
- GitHub: [Your GitHub Link]

---
**Enjoy your containerized applications! 🚀**
