# MediSafe AI Frontend

The root `index.html` is the public landing page. Vercel rewrites send API, login, customer, and admin requests to the Django backend at `https://analyticsbackend.vercel.app` while keeping the browser on this frontend domain.

## Vercel setup

1. Import the `analytics_backend` GitHub repository as a separate Vercel project and name the project `analyticsbackend` so its production URL matches the rewrite target.
2. Set the backend project's Root Directory to the repository root and keep the Django framework preset.
3. Add `DJANGO_SECRET_KEY` for Production and Preview. Set `DJANGO_DEBUG=0` for Production. Redeploy the backend and confirm its production URL responds before testing login or API features.
4. Deploy this repository as a static frontend project with its repository root as the Root Directory.

The backend trusts `https://analyticsfrontend.vercel.app` for CSRF requests from this frontend. Add any preview or custom frontend origins to `DJANGO_CSRF_TRUSTED_ORIGINS` in the backend project's environment variables.
