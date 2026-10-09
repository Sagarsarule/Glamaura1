# GLAM AURA feature status (current build)

This file distinguishes features that work in the current code from ideas that are not yet implemented. Do not describe planned features as completed in a project report or viva.

## Available in this build
- Artist discovery cards and profile modal: name, specialization/style, bio, Instagram, distance when browser location is granted, and verification state (currently demo artists may show as not verified).
- Portfolio display and artist image upload, saved as media records and files.
- Service selection with server-side prices.
- Server-checked appointment slots and conflict protection for active bookings.
- Customer/artist account signup and login, bcrypt password hashing, cookie-based sessions stored in SQLite.
- Booking creation and booking history. Customer accounts see their bookings; artist accounts see bookings linked to their artist profile. The new Bookings & appointment updates section displays server-returned booking statuses.
- Razorpay checkout when valid environment credentials are configured; otherwise the app uses its explicitly labelled demo payment flow.
- Customer reviews tied to confirmed bookings.
- Nearby artist map integration code; a Google Maps API key and correct deployment configuration are needed for the live map.
- Contact form, visitor counter, privacy policy and terms pages.
- Supplied GLAM AURA brand artwork is cropped to `assets/glam-aura-logo.svg` and displayed in the navigation header.

## Partially implemented
- Artist dashboard: artist account can upload portfolio media and view bookings in the new booking-history section. It does not yet support accepting/rejecting requests or editing services.
- Availability: customers can view server-checked slots, but the available times are a fixed configured list. Artists cannot yet add, edit or block their own dates/time windows.
- Verification: a verification field is stored and shown in artist profile data, but there is no admin workflow to review documents or change verification state.
- Notifications: booking/payment results and statuses are displayed in the website; email, SMS, push notifications and a persistent notification centre are not implemented.

## Not implemented yet
- Admin dashboard and role-protected admin login.
- Admin artist verification workflow.
- Admin user management.
- Admin reports/analytics dashboard.
- Artist actions to accept/reject/cancel bookings or manage availability.

These admin and management features should be implemented with server-side authorization and database changes before they are presented as functional. They are intentionally not represented as fake buttons or fake admin screens in this build.


## Implemented in version 4.0.0 (Glam Aura rename)
- Rebranded customer-facing website title, copy, favicon and navigation logo to Glam Aura.
- Artist availability management: block or reopen standard time slots on specific dates; slot API honours overrides.
- Artist booking actions: accept, reject, or mark confirmed appointments completed.
- Protected administrator workspace with database summary, user activation/deactivation, artist verification, booking overview and booking reports.
- In-app notifications for booking creation, payment confirmation, artist actions and verification status.
- Optional administrator bootstrap via ADMIN_EMAIL and ADMIN_PASSWORD environment variables (password minimum 12 characters).

## Still not included / production caveats
- Email/SMS/push delivery is not configured; notifications are in-app only.
- Refunds are not automatically issued when a booking is rejected after payment; the UI warns support handling is needed.
- Payment mode is demo unless valid Razorpay credentials and production webhook/verification configuration are supplied.
- Artist verification is an admin decision in this prototype and does not automatically validate government documents.
- Availability uses the platform's five standard daily times; custom time creation and recurring schedules are not included.
- Revenue reports sum confirmed/completed booking amounts; they are not accounting-grade settlement reports.
