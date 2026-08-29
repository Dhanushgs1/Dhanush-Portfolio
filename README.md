# Dhanush G, Personal Portfolio

A single-page personal portfolio built with plain HTML, CSS and vanilla
JavaScript. No build step, no framework, no dependencies beyond a Google Fonts
stylesheet and an icon set.

Several tab-style pages live in one document and are switched client-side. A
fixed sidebar carries the profile, contact details and social links, and
collapses behind a toggle on mobile.

## Running it

Open `index.html` in a browser. That is the whole setup.

To serve it over HTTP instead:

```bash
python -m http.server 8000
```

## What is on it

Six `[data-page]` sections are in the markup:

| Section      | Contains                                                    |
| ------------ | ----------------------------------------------------------- |
| About        | Intro and services.                                          |
| Resume       | Education and experience timeline.                           |
| Projects     | Filterable project grid linking to the GitHub repositories.  |
| Books        | Reading list.                                                |
| Client works | Client work samples.                                         |
| Location     | An embedded Google Map of Tirunelveli, Tamil Nadu.           |

The navbar exposes three of them: About, Resume and Projects. Page switching
matches the clicked link's text against each section's `data-page` value, so
Books, Client works and Location are in the document but have no way to be
opened until a matching navbar link is added.

Project cards link out to `Driver-Behavior-Detection-CNN`,
`MNIST-Handwritten-Digit-Classification-Dataset.`,
`Predicting-Housing-Prices-Using-Linear-Regression`, `Restaurant` and
`Vending-Machine-Design-Low-Level`.

## How the JavaScript works

`script.js` is 138 lines and does everything with `classList.toggle`:

- **Sidebar** opens on mobile via `[data-sidebar-btn]`.
- **Page switching** compares navbar link text to `data-page` and marks one
  section active. Nothing is routed, so the URL never changes and individual
  pages are not linkable or bookmarkable.
- **Project filter** shows or hides `[data-filter-item]` cards by category,
  driven by buttons on desktop and a custom select on mobile.
- **Testimonial modal** copies a clicked card's avatar, title and text into a
  shared modal. No testimonial cards are currently in the markup, so this
  handler never fires.

## Layout

```
index.html    Every page, as sibling [data-page] sections
style.css     All styling, including the responsive breakpoints
script.js     Sidebar, page switching, project filter, modal
```

Images and the resume sit in the repository root and are referenced by relative
path.

## Notes

- The resume and one project link point at Google Drive download URLs, which
  break if those files are moved or their sharing is revoked.
- Several `href=""` placeholders remain in the markup; those links reload the
  page instead of navigating.
