# MediSafe AI Frontend

The root `index.html` is the public landing page. Vercel rewrites send API, login, customer, and admin requests to the Django backend at `https://analytics-backend-1-4i7z.onrender.com` while keeping the browser on this frontend domain.

## Vercel setup

1. Deploy the `analytics_backend` repository as a Render Web Service from branch `main`, with the repository root as Root Directory.
2. Set the Render variables `DJANGO_SECRET_KEY` and `DJANGO_DEBUG=0`. The backend reads its Render hostname automatically and trusts this frontend's origin for CSRF.
3. Deploy this repository to Vercel as a static frontend project with its repository root as Root Directory. Its `vercel.json` proxies API and account routes to the Render service.

The backend trusts `https://analyticsfrontend.vercel.app` for CSRF requests from this frontend. Add any preview or custom frontend origins to `DJANGO_CSRF_TRUSTED_ORIGINS` in Render's service Environment settings.
