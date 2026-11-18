# WellNest Supabase Authentication Setup

The `index.html` branch now contains an email/password sign-up and login interface powered by Supabase Auth. Complete these one-time steps before testing it.

## 1. Create a Supabase project
1. Open https://supabase.com/dashboard and create a project.
2. In Project Settings → API (or the project's Connect/API settings), copy the **Project URL** and the **publishable key** (or legacy **anon** key).
3. Do not use or expose the `service_role` / secret key in browser code.

## 2. Configure the website
Open `index.html` and replace:
- `YOUR_SUPABASE_PROJECT_URL` with the Project URL.
- `YOUR_SUPABASE_PUBLISHABLE_OR_ANON_KEY` with the publishable/anon key.

These are intended for browser use when Supabase Row Level Security (RLS) is correctly configured. Never put private service-role keys in this file.

## 3. Configure email authentication
In Supabase Authentication → Providers → Email, enable email/password sign-in. Keep email confirmation enabled for real accounts.

In Authentication → URL Configuration, add your deployed GitHub Pages URL to the allowed Site URL / Redirect URLs, for example:
`https://aryandevraj.github.io/WellNess_Project_CSE326_/`

## 4. Test
1. Open the deployed site.
2. Create an account with an email address you can access and a password of at least 8 characters.
3. Confirm the email if confirmation is enabled.
4. Switch to Log in, sign in, and then test Log out.

## What this change does
- Adds a dedicated Account section with sign-up, login, session display, and logout.
- Uses Supabase Auth rather than storing passwords in the website.
- Uses Supabase-managed sessions and automatic token refresh.
- Keeps the existing WellNest activities and page content.

## Important limitations
- The account feature will remain disabled until you add the Supabase project URL and publishable/anon key.
- Existing activity registration, reminders, reports, and contact forms are still demo forms; they are not saved to a database by this authentication change.
- This does not add user-specific access control to activity data. If you later add private database tables, enable and test Row Level Security policies.
