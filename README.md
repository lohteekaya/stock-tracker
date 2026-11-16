# Outlet performance dashboard

Single-page dashboard (`index.html`, no build step) showing weekly sales vs target per outlet.
Data and sign-in come from Supabase (table `public.outlet_weeks`, Supabase Auth).

## Deploy to Vercel

1. In Vercel: **Add New → Project → Import** this GitHub repo.
2. Framework Preset: **Other**. Leave Build Command and Output Directory empty (`vercel.json` already sets them).
3. Click **Deploy**.

No environment variables are needed. The Supabase project URL and **publishable** key are in
`index.html`; they are designed to be public. Access is controlled by Row Level Security:
only signed-in users can read `outlet_weeks`, and nobody can write from the browser.
Never put a Supabase `service_role` / secret key in this file.

## Sign in

Usernames map to `username@outlet-dashboard.example` (see `EMAIL_DOMAIN` in `index.html`).
Create users in the Supabase dashboard under **Authentication → Users** using that email pattern
(tick "Auto Confirm User"); a profile row is created automatically.
Change the initial passwords after first sign-in.
