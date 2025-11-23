# Railway Deployment Guide

This Game of Life application is configured to run on Railway.

## What Changed

- **package.json**: Updated with `serve` package and Railway-compatible scripts
- **nixpacks.toml**: Railway build configuration
- **Procfile**: Process configuration for Railway
- **railway.json**: Railway-specific deployment settings

## How to Deploy

### Option 1: Deploy from GitHub (Recommended)

1. Push this code to your GitHub repository
2. Go to [Railway](https://railway.app/)
3. Click "New Project"
4. Select "Deploy from GitHub repo"
5. Select this repository
6. Railway will automatically detect the configuration and deploy

### Option 2: Deploy using Railway CLI

1. Install Railway CLI:
   ```bash
   npm i -g @railway/cli
   ```

2. Login to Railway:
   ```bash
   railway login
   ```

3. Initialize and deploy:
   ```bash
   railway init
   railway up
   ```

## Configuration

The application serves the Game of Life visualization from the `public` directory on the port provided by Railway (via the `PORT` environment variable).

- **Start Command**: `npm start`
- **Build Command**: Not required (static files)
- **Port**: Automatically assigned by Railway via `$PORT` environment variable

## After Deployment

Once deployed, Railway will provide you with a URL like `https://your-app.railway.app`. Point your 3 wall-mounted screens to this URL to display the Game of Life visualization.

## Local Development

To run locally:
```bash
npm install
npm start
```

The app will be available at `http://localhost:3000`
