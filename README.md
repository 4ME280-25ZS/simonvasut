# Wishlist (GitHub Pages + Supabase)

This repository provides a static wishlist page where each product can be claimed by one person. Claims are stored in Supabase (Postgres).

## Supabase setup
1. Create a Supabase project at https://app.supabase.com.
2. In the SQL editor, create a `products` table with the following schema:

```sql
create table if not exists products (
  id text primary key,
  name text,
  claimed_by text,
  claimed_at timestamptz
);
```

3. In the Project Settings → API, copy the `URL` and the `anon` public key.
4. In `index.html` replace `SUPABASE_URL` and `SUPABASE_ANON_KEY` placeholders with your values.

## Security
- The `anon` key allows client access; secure critical operations via Row Level Security (RLS) policies.
- Example RLS: allow anyone to read, but only authenticated users to write. See Supabase docs for RLS and Auth.

## Deploy to GitHub Pages
1. Create a GitHub repository and push the contents of this folder.
2. In GitHub → Settings → Pages, select the branch and folder to publish (e.g. `main` branch, `/` root).
3. After publishing, your site will be live.

## Local testing
To serve locally:

```powershell
cd C:\Users\simon\Documents\skola\webdesign\simonvasut
python -m http.server 8000
# Open http://localhost:8000 in your browser
```

## Next steps (recommended)
- Enable Supabase Auth and update RLS policies so only authenticated users can claim.
- Add an "unclaim" action and confirm dialogs.

If you want, I can add example RLS policies and a simple auth flow — should I proceed?