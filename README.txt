GLAM AURA 4.0 - MAKEUP ARTIST DISCOVERY & BOOKING PLATFORM

RUN LOCALLY
1. Install Node.js 22.5 or newer. This build uses Node's built-in SQLite support, so you do not install SQLite separately.
2. Open this GLAM AURA_PREMIUM folder in VS Code.
3. In Terminal run: npm install
4. Start the backend: npm start
5. Open: http://localhost:3000

IMPORTANT
Do NOT open glamindex.html by double-clicking it or with a generic Live Server extension. Authentication, SQLite, slots, bookings and the visitor counter are server features. The Express server must serve the page.

DEMO ACCOUNTS
Created automatically on the first successful server start if they do not already exist:
Customer: customer@glamaura.demo / demo123
Artist:   artist@glamaura.demo / demo123

REAL ACCOUNTS
Use Create account in the website. The password is stored as a bcrypt hash in SQLite. A persistent HTTP-only session cookie is created for 30 days. When you return using the same browser, GLAM AURA checks that session and shows your account as logged in. Logging out removes the session.

DATABASE
The server creates glamora.sqlite automatically. Tables include users, sessions, artists, bookings, reviews, contact_messages, media, site_stats, slot_overrides and notifications. Do not edit password hashes manually.

GOOGLE MAPS
1. Create/select a project in Google Cloud Console.
2. Enable Maps JavaScript API.
3. Attach billing to the project when using the standard production API key.
4. Create an API key.
5. Restrict the key to Websites / HTTP referrers. For local testing allow http://localhost:3000/* . When your custom domain is connected, add https://YOUR-DOMAIN/* too.
6. Under API restrictions, allow Maps JavaScript API.
7. Copy .env.example to .env.
8. Put your key on this line: GOOGLE_MAPS_API_KEY=YOUR_KEY
9. Restart npm start.

The frontend loads the key from /api/config and then loads the Google Maps JavaScript API. Browser geolocation calculates the user's distance to the artist coordinates. If you later add address search/autocomplete, enable the appropriate Places API as well.

RAZORPAY
Leave RAZORPAY_KEY_ID and RAZORPAY_KEY_SECRET empty for demo payment mode. Add real credentials only when you are ready for live payments.

HIT COUNTER
The only intentionally seeded metric is the GLAM AURA hit counter. It starts at 100 in SQLite and increments through /api/counter.

LAUNCH CHECKLIST
Custom HTTPS domain, favicon, privacy policy, terms and conditions, real payment credentials, restricted Google Maps key, production database backup strategy, final browser/mobile testing, and removal of all demo content before public launch.


ADMINISTRATOR SETUP
-------------------
Set ADMIN_EMAIL and ADMIN_PASSWORD in your .env or hosting environment. Use a unique password of at least 12 characters. On startup the server provisions that account with administrator access. Never publish the password or commit .env. Open /workspace.html after logging in with that account.

ARTIST WORKSPACE
----------------
Log in using an artist account and open /workspace.html to manage availability, review incoming bookings and view notifications. Artists can block/unblock standard time slots for specific dates.

ADMIN WORKSPACE
---------------
The administrator workspace includes database-driven summary metrics, artist verification, user activation/deactivation, booking overview and monthly/status reports. Admin APIs are protected by the is_admin flag on the account, not by a hidden front-end button.

NOTIFICATIONS
-------------
Booking lifecycle events create in-app notifications. Email and SMS delivery are not configured in this project.
