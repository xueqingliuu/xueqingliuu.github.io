# Website Redesign — Design Direction & Content Strategy

Xueqing Liu · xueqingliuu.github.io · September 2026

This document explains the thinking behind the redesign that now lives in your site folder, and gives you a playbook for keeping the site sharp as your career grows.

## 1. Design direction: "warm scholarly minimal"

The goal is a site that reads as *considered* rather than *templated* — distinctive enough to be memorable, restrained enough to be credible.

**Typography.** Headings and paper titles are set in Source Serif 4, a contemporary serif with academic warmth; body text is Inter, a highly legible sans. The serif/sans pairing is what gives the site its character: serif signals scholarship, sans keeps reading comfortable on screens. Body text is 17px with a 1.65 line height — noticeably more comfortable than the jemdoc default.

**Color.** A warm off-white ground (`#FBF9F5`) instead of stark white, warm near-black text (`#2B2723`), and exactly one accent: a deep scholarly crimson (`#96222E`) — a quiet nod to Harvard without being literal. The accent is used sparingly (links, venue badges, timeline dots, news dates), which is what keeps the page calm. All color pairs meet WCAG AA contrast.

**Spacing and surfaces.** Content sits in a single 44rem column with generous vertical rhythm. Publications, research interests, and the contact block sit on white cards with hairline borders and soft radii — enough structure to scan quickly, no shadows or gradients competing for attention.

**Imagery.** One circular portrait in the hero, nothing else. Academic sites don't need stock imagery; your photo plus disciplined typography does the work.

## 2. Site map

```
index.html          Home: hero → about → research interests → news
                    → selected publications (3) → contact
publication.html    All publications: preprints & under review / published
talks.html          Talks grouped by year, timeline style
contact.html        Now a redirect to index.html#contact
                    (it previously contained leftover jemdoc author contact info)
```

Navigation is a simple top bar — Home, Publications, Talks, Contact — with the current page marked both visually and with `aria-current`. Four items is the sweet spot; every visitor type (collaborator, student, recruiter, organizer) finds their path in one glance.

## 3. Content strategy

**Homepage as an executive summary.** The homepage now answers, in order and within one scroll: who you are, what you work on, what's new, what your best work is, and how to reach you. Each section links out rather than expanding in place, so nothing overwhelms.

**Bio.** The About text was lightly rewritten so the first paragraph leads with what your research *does* ("deciding when, whom, and how to nudge, and measuring whether it worked") before the credentials. Visitors who read only two sentences still leave knowing your expertise.

**Research interests with one-line explanations.** Each of your four areas now carries a plain-language sentence. This is the single highest-leverage change for non-specialist visitors (recruiters, prospective students, journalists).

**News without maintenance burden.** The News list is four dated lines. Convention: keep the six to eight most recent items, prune the rest yearly. Add an item whenever a paper is accepted, a talk is given, or an award lands. Two dates are my best inference — please verify the "Joined Harvard (2024)" entry and adjust.

**Selected vs. all publications.** Three first-author or flagship papers on the homepage; the full list stays on its own page, split into "Preprints & Under Review" and "Published Papers," with your name bolded, venue-year badges, and pill links (Journal / arXiv / SSRN). When you have PDFs, slides, or code, add more pills to the same `pub-links` span.

**Talks as a timeline.** Grouped by year with Invited/Contributed badges — the badge distinction quietly signals recognition without a boast.

**Recommended next additions** (structure is ready for them): a CV page or a `cv.pdf` link in the nav; a "Software" section if you release R/Python packages; per-paper `[Abstract]` toggles only if the list grows past ~20 entries.

## 4. Accessibility and mobile

The rebuild is semantic HTML5 (`header/nav/main/section/footer`, real lists, one `h1` per page) with a skip-to-content link, visible focus outlines, `alt` text on the portrait, `aria-current` navigation state, AA contrast throughout, and `prefers-reduced-motion` respected. Below 640px the hero stacks, interest cards go single-column, and news dates move above their text. There is no layout JavaScript at all — the old hamburger/reload script is gone, so the site is faster and can't break.

## 5. Interactive elements — deliberately few

For an academic site, restraint *is* the feature. What's included: hover states on cards and pills, smooth-scroll to #contact, and your existing tawk.to chat widget (kept per your choice; if you ever find it distracting, deleting the script block at the bottom of each page removes it). I'd advise against carousels, animations on scroll, or visitor counters — they cost credibility.

## 6. Housekeeping notes

- **Old files.** `main.css`, `nomenu.css`, `table.css`, `jemdoc*`, `mathjax.html`, `tables.html`, and `menu.html` are no longer referenced. They're harmless, but you can delete them for a cleaner repo (git history keeps everything).
- **MathJax** was removed since no current page uses math. If you add math later, re-add one script tag: `<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js" async></script>`.
- **Fonts** load from Google Fonts with system-font fallbacks, so the site still renders well offline.
- **Publishing.** Nothing has been pushed. Preview locally by opening `index.html`, then `git add -A && git commit && git push` when you're happy.
- **Footer date.** Update "Last updated" when you make meaningful changes — it signals the site (and you) are active.

## 7. Example copy you can reuse

One-line intro (for the hero or elsewhere): *"I develop statistical and machine learning methods that make digital health interventions smarter."*

News item template: `Mon YYYY — "Paper title" accepted at Venue.` / `Mon YYYY — Invited talk at Venue, City.`

Contact invitation (already on the site): *"I am happy to hear from prospective collaborators, students, and conference organizers."*
