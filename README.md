# Mesa — deploy to Vercel

Two files. `index.html` is the whole site. Everything below takes about fifteen minutes.

---

## 1. Put it online (5 minutes, no database yet)

1. Go to **vercel.com** and sign in with GitHub, GitLab or email.
2. Click **Add New → Project → Deploy without Git** (or drag the folder onto the dashboard).
3. Drop this folder in. Vercel sees `index.html` and treats it as a static site — no framework, no build step, no settings to change.
4. Hit **Deploy**. You get a URL like `mesa-xyz.vercel.app`.

That link works for anyone. Share it, QR-code it, put it on a slide.

At this point the site is fully usable but has no shared database — each person's answers stay in their own browser and the **Data** tab stays empty. Step 2 fixes that.

**Alternative if you prefer GitHub:** push this folder to a repo, then in Vercel choose **Import Git Repository**. Every push then redeploys automatically, which makes step 2 easier.

---

## 2. Add the database (10 minutes)

Supabase is free and needs no server code.

### Create the project
1. Go to **supabase.com**, sign up, click **New project**.
2. Name it `mesa`, pick any region near you, set a database password (you won't need it again), create.
3. Wait about a minute while it provisions.

### Create the table
Open **SQL Editor** in the left sidebar, paste this, and hit Run:

```sql
create table mesa_events (
  id bigint generated always as identity primary key,
  kind text not null,
  payload jsonb not null,
  created_at timestamptz default now()
);

alter table mesa_events enable row level security;

-- the public site may WRITE
create policy "anyone can insert"
  on mesa_events for insert to anon with check (true);

-- and deliberately NO read policy.
-- Nobody can read the table with the public key. Only your
-- service key (which never leaves your machine) can.
```

### Get your two keys
Go to **Project Settings → API**. Copy:
- **Project URL** — looks like `https://abcdwxyz.supabase.co`
- **anon public** key — a long string starting `eyJ...`

### Paste them in
Open `index.html`, find this block near the top of the `<script>` (around line 674):

```js
var SUPABASE_URL = "";
var SUPABASE_KEY = "";
var TABLE        = "mesa_events";
```

Fill in the first two. Save. Redeploy to Vercel.

### Check it worked
Open your site. Top right should say **Saving** with a green dot. Go through a sign-up — that's a row written.

---

## 3. Your private dashboard

There is no Data tab on the public site. It isn't hidden with a password — it genuinely cannot be read with the key in the deployed code.

**To open it:** add `#data` to your URL.

```
https://your-site.vercel.app/#data
```

It asks for your **service_role** key — Supabase → Project Settings → API, below the anon key. Paste it and the dashboard unlocks.

That key lives in `sessionStorage` for that browser tab only. It is never in the deployed files, never in your repo, and gone when you close the tab. Nobody else can open the dashboard, even knowing the `#data` address, because they don't have the key.

**Never paste the service_role key anywhere else** — not into `index.html`, not into a repo, not into a group chat. It bypasses every rule on your database.

### Export for analysis

Two buttons at the top of the dashboard:

- **Export to Excel** → a real `.xlsx` with one sheet per collection (signups, choices, rounds, feedback, appfeedback). Pivot straight from it.
- **Export as CSV** → one file with all five sections, UTF-8 so accents survive.

Both include a `_at` timestamp column on every row, so you can chart things over time.

---

## How the data is stored

One table, one row per event. The `kind` column says what it is:

| kind | written when |
|---|---|
| `signups` | someone finishes onboarding |
| `choices` | a dish is picked or changed |
| `rounds` | someone submits their grateful / hard |
| `feedback` | the evening feedback form |
| `appfeedback` | the app feedback form |

The **Data** tab reads all of it back and does the counting in the browser. It refreshes when you open the tab and every 12 seconds while you're on it.

To look at raw rows, use **Table Editor → mesa_events** in Supabase. You can export to CSV from there if you want the numbers in a slide.

---

## Two things worth knowing

**The anon key is public, and that's fine.** It sits in browser code by design. With the policy above it can only INSERT — someone who copies it could add junk rows, but cannot read a single thing anyone has written. That's the trade-off worth understanding: write access is open, read access is yours alone.

**The round entries are the sensitive part.** People write real things there. The Data tab keeps them behind a "Show entries" button — don't click it on a projector.
