# Mesa: a weekly table for students who just moved 🍅🥕🌿

**"You just moved. Nobody knows you yet. Until Wednesday."**

Our answer to the SoReDI challenge *youth loneliness in the age of AI*: students cook a dish from home together on Saturday, then four kitchens share one table on Wednesday. Built and tested in the **CEMS × SoReDI Design Sprint** (*Creative Design Thinking*) at ESADE Business School, Barcelona, 15–18 Sep 2026.

**Team 3:** Linus · Rita · João · Paul · Niki · Ameer

[![Open the live app](https://img.shields.io/badge/Live-mesa--boy5.vercel.app-111?style=for-the-badge&logo=vercel)](https://mesa-boy5.vercel.app)
[![Case study](https://img.shields.io/badge/Read-Case%20study-2a78d6?style=for-the-badge)](https://ameer29.github.io/mesa.html)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white)

---

## 1 · Problem: one in four is lonely, and AI answers first
- **25.5%** of 16–29-year-olds in Spain feel lonely (ONCE, 2024), and it peaks right after a move. Welcome week is a blur of names, and by week three the groups have closed.
- AI is the faster option. It's awake at midnight, it agrees with you, and it ends the conversation feeling resolved. Across our interviews that meant **real comfort but no relationship**. As one interviewee put it: *"Closure was faster."*
- Nobody in six interviews used the word "lonely". They all said "busy".

## 2 · User: Giulia, 23, from Milan, month 2 of 5 on exchange
A persona synthesised from six interviews (one run by each teammate). Her programme friends feel temporary ("we're all leaving anyway"). She doesn't want 600 contacts; she wants **two people** and somewhere to turn up on a Wednesday.

## 3 · Solution: a weekly table, not another app to perform on
| | |
|---|---|
| **Cook** | Six students from one university, verified by university email, cook a dish from home together. The task carries the conversation. |
| **Table** | Four kitchens bring their dishes to one shared table, at a new venue every week. |
| **The round** | Everyone names one thing they're grateful for and one thing that's hard. No fixing, and no advice unless someone asks. |

## 4 · Iteration: seven tests, four changes
We used the Explorative Experimentation Cycle (Hassi & Rekonen, 2018): 6 hypotheses, a 10-question script, and 6 student testers plus 1 AI walkthrough.

| Finding | Change |
|---|---|
| Nobody trusts a free sign-up | Ingredients paid upfront (**€5–8**): commitment, not revenue |
| Hosting alone is the real ask, and safety is about people | Verified profiles and the guest list shown first, plus a co-host or a neutral kitchen |
| A download is a barrier | A web app launched through the university |
| Diets and seating | Post-dinner ratings feed the seating; a recipe-and-budget matcher handles diets |

**Kept untouched:** cooking together and the round. Every tester liked them.

## 5 · Final: Mesa v2 and the ask
Sign up → profile → book and pay → see the host and guest list → cook, eat, do the round → rate and swap contacts.
**Pilot ask:** four tables at ESADE in week three of the semester. **Success metric:** how many people book a second table.

---

## My role
- **Design thinking with the team:** our Miro board covered the context map, research plan, user interviews (I ran Interview 6), empathy map, problem statement, How-Might-We, ideation, paper prototype and experiment plan.
- **I owned the website.** When we split the work, I built this web app from the first clickable prototype (tested with students on Day 3) to the live version. I deployed it on **Vercel** and connected **Supabase** to collect real data from ESADE students: sign-ups, dish choices, round entries, and feedback on the evening and the app.

## What's in the app
A 6-step onboarding (university email, home country, what brings you here, cooking level) · table matching (simulated in the prototype; the planned logic uses diet, budget and neighbourhood) · dish picks · a weekly plan (shopping list, swappable roles, recipe video) · the round · a group thread that stays open between weeks · feedback forms · a private admin dashboard with Excel/CSV export.

## Tech
- Single-page app: **HTML, CSS and vanilla JavaScript** (index.html)
- **Vercel** hosting · **Supabase** (Postgres) for data collection
- The admin dashboard needs the service key, which is never stored in this repo; the public key in the code is the restricted anon key.

## Deploying
See [DEPLOY.md](DEPLOY.md).

---
Part of my portfolio · **[ameer29.github.io](https://ameer29.github.io)**
