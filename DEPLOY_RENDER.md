# GLAM AURA deployment

## Staging deployment

GLAM AURA is an Express web service, so deploy it as a Render **Web Service**, not a Static Site. The included `render.yaml` configures Node, the start command, `/api/health`, environment variables, and a persistent disk for SQLite and uploads.

### Important

A persistent disk is required if you want SQLite accounts, sessions, bookings, and uploads to survive Render restarts and redeploys. Render documents persistent disks as a paid feature. Do not remove the disk if persistent data matters.

### Steps

1. Put the contents of `GLAM AURA_PREMIUM` in a GitHub repository.
2. In Render, create a Blueprint from that repository, or create a Web Service and use the same settings.
3. Use Node as the runtime.
4. Build command: `npm install`
5. Start command: `npm start`
6. Health check: `/api/health`
7. Persistent disk mount: `/var/data`
8. SQLite path: `/var/data/glamora.sqlite`
9. Upload path: `/var/data/uploads`
10. Add `GOOGLE_MAPS_API_KEY` in Render Environment Variables.
11. Leave `GOOGLE_MAPS_MAP_ID=DEMO_MAP_ID` for testing, or replace it with your own production Map ID.
12. Deploy and open the generated `onrender.com` URL.

The generated Render URL is a **staging URL**. Do not call it the final launch while the custom domain and production configuration are unfinished.

## Google Maps setup

Create a Google Cloud project, enable Maps JavaScript API, create an API key, and restrict the key to the GLAM AURA website/domain. Google requires an API key for standard Maps JavaScript API use and recommends API/application restrictions.

For local testing, a browser origin such as `http://localhost:3000/*` can be allowed. For staging, add the Render hostname. For final launch, add the custom HTTPS domain.

The frontend uses Google Maps Advanced Markers. Google requires the marker library and a Map ID for Advanced Markers; `DEMO_MAP_ID` is suitable for testing. Create a production Map ID before final launch.

## Production launch gate

Before changing `NODE_ENV` to `production`, set `PUBLIC_BASE_URL` to the connected HTTPS custom domain. The server intentionally refuses production startup without that value.

Also complete:

- custom domain
- favicon
- Privacy Policy
- Terms and Conditions
- restricted Google Maps API key
- real Razorpay credentials if live payments are required
- final authentication, booking, slot, payment and map tests
