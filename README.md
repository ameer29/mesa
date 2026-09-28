# Mesa: cook together, eat wider 🍅🥕🌿

**Our answer to the brief "Youth, loneliness in the age of AI": a live web app that matches newly arrived university students into mixed-nationality groups of four who cook one dish together, then meet at a shared table every week.**

Design-thinking group project · *Creative Design Thinking*, ESADE Business School (CEMS exchange) · Barcelona · 2026

[![Open the live app](https://img.shields.io/badge/Live-mesa--boy5.vercel.app-111?style=for-the-badge&logo=vercel)](https://mesa-boy5.vercel.app)
[![Case study](https://img.shields.io/badge/Read-Case%20study-2a78d6?style=for-the-badge)](https://ameer29.github.io/mesa.html)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white)

---

## The problem
*"You just moved. Nobody knows you yet."* Students who move to a new city start with no network, and apps make it easy to stay in. We focused on the first weeks after arrival, when isolation sets in fastest.

**Design principle:** technology should organise the meeting, not replace it.

## How Mesa works
| Step | What happens |
|---|---|
| 1 · Join | Sign up with your **university email**; Mesa runs inside one university |
| 2 · Match | A table of **four students from four countries**, so nobody has the home advantage |
| 3 · Pick | One dish from each person's country, plus easy options |
| 4 · Saturday | Cook together at the host's flat: shopping list, swappable jobs, recipe video |
| 5 · Wednesday | Four kitchens, one table, a new venue each week |
| 6 · The round | Each person names **one thing they're grateful for and one thing that's hard**. No fixing, just listening |

A group thread stays open between weeks; XP and badges reward showing up.

## Process
Context map canvas → user personas and interviews → team brainstorming (the course's design-thinking method) → website **v0** → **v1 live with ESADE students**.

## My role
I took part in the brainstorming and design-thinking process with the team. When we split the work, I took on **the website**: I built it from version 0 to a live version 1, deployed it on **Vercel**, and connected **Supabase** to collect real data from ESADE students (sign-ups, dish choices, round entries, and feedback on the evening and the app).

## Tech
- Single-page app: **HTML, CSS and vanilla JavaScript** (index.html)
- **Vercel** hosting · **Supabase** (Postgres) for data collection
- Private admin dashboard with Excel/CSV export. It needs the service key, which is never stored in this repo; the public key in the code is the restricted anon key.

## Deploying
See [DEPLOY.md](DEPLOY.md).

---
Part of my portfolio · **[ameer29.github.io](https://ameer29.github.io)**
