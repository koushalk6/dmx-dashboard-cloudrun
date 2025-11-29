# DMX Dashboard — React + Tailwind (Google Cloud Run ready)

This repo is a small React + Tailwind UI that looks like the DMX dashboard
screenshots you provided. It is **100% compatible with Google Cloud Run**:

- Uses Node 20 (LTS) official image
- Uses a simple Express server for static files
- Standard `PORT=8080` (Cloud Run default)
- Multi-stage Dockerfile builds and serves the production bundle

## Local development

```bash
npm install
npm run dev
```

Visit http://localhost:5173

## Build locally

```bash
npm run build
npm run preview
```

## Deploy to Google Cloud Run (from this repo)

1. Create a new GitHub repo and push these files.
2. In Google Cloud Console:
   - Go to **Cloud Run → Create service**
   - Choose **Deploy from source**
   - Connect your GitHub repo
   - Select the default build settings (Cloud Build will detect the Dockerfile)
3. Use:
   - Region: any supported
   - CPU/Memory: default is fine
   - Allow unauthenticated invocations (if you want a public URL)

Cloud Run will:

- Build the Docker image using `Dockerfile`
- Run the container with `PORT=8080`
- Serve the React app from `/`

You don't need to change versions or config. Everything here is
compatible with Cloud Run's Node 20 runtime and standard Docker flow.
