# 🕷️ Web Scraper + Flask Server (Multi-stage Docker Build)

This project scrapes a website using Puppeteer in a Node.js environment, saves the data, and serves it through a Flask API in Python — all wrapped in a multi-stage Docker container.

## 📦 What's Inside?

- **Node.js + Puppeteer**: Headless browser scraping.
- **Python + Flask**: Lightweight API server to serve scraped data.
- **Docker Multi-Stage Build**: Efficient, clean image with isolated concerns.

## 🧾 Project Structure
.
├── Dockerfile

├── package.json

├── requirements.txt
├── scrape.js
├── server.py
└── scraped_data.json (generated during build)

## 🛠️ How It Works

1. **Stage 1: Scraper**
   - Node.js and Puppeteer are used to scrape the `<title>` and first `<h1>` from a given URL.
   - The data is saved into `scraped_data.json`.

2. **Stage 2: Server**
   - A minimal Flask app reads the `scraped_data.json` file and serves it via an HTTP endpoint.

## 🚀 Getting Started

**Clone the Repository**
git clone <GitHub-repo-url>
cd <repo-url>

**Build the Docker Image**
docker build --build-arg SCRAPE_URL=https://example.com -t scraper-server .
> Replace `https://example.com` with any URL you'd like to scrape.

### 3. **Run the Container**
docker run -p 5000:5000 scraper-server
```

Access the Application

http://localhost:5000/
```
## 📄 Example Output

```json
{
  "title": "Example Domain",
  "heading": "Example Domain"
}
```
## 🧹 Clean Up

To stop and remove the running container:

docker ps
docker stop <container_id>
docker rm <container_id>
