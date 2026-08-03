---
name: frontend
description: Rules for anything that renders HTML — accessibility, SEO and GEO built as one job for the non-visual reader. Use when writing or reviewing HTML, templates, components, ARIA, meta tags, structured data, sitemaps, llms.txt, or any page a browser, crawler or agent will read.
user_invocable: true
---

# Frontend

Anything that renders HTML. **Accessibility, SEO and GEO are one job** — a screen reader, a
crawler and an agent are all non-visual consumers of the same structure. Build for that
reader and the other two follow; build for sighted humans only and all three fail together.

- **Semantic HTML first, roles second.** The right element, not a `div` with a role bolted
  on. A role is for when no element says it, never a substitute for one that does.
- **Names, not decoration.** Every control has an accessible name saying what it does; markup
  carrying its own `aria-label` outranks any default I generate.
- **Keyboard is not optional.** Reachable, operable, no traps. Say what a key does where the
  user is, not in a legend elsewhere.
- **Heading hierarchy is the document outline**, and how every machine reader navigates. Do
  not pick a level for its size.
- **Landmarks and one `<main>`**, skip links where the nav is long.
- **SEO is metadata plus structure**: title, description, canonical, Open Graph, sitemap, and
  headings that describe rather than tease.
- **GEO is being quotable.** Generate `llms.txt` — poops does it natively. Content must
  survive extraction: state the fact in the sentence, not in the design.
- **Structured data where it is true.** Schema.org for what a page genuinely is — a lie in
  JSON-LD is a lie that ranks.
- **Degrade honestly**, as everywhere: no JS, no webfont, no CSS, the page still reads —
  which is also what makes it cheap for an agent to parse.
