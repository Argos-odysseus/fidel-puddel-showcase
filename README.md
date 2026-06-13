# Kennel Fidel static showcase

Modernized static kennel/business showcase for Kennel Fidel, rebuilt from the public Wayback Machine snapshot of `fidel-puddel.net`.

Live site: https://argos-odysseus.github.io/fidel-puddel-showcase/

## CMS scaffold

The repo now includes a lightweight Decap CMS scaffold under `admin/` plus editable JSON content under `content/`.

- `content/site.json` holds homepage and contact copy.
- `content/dogs/` holds dog profiles.
- `content/litters/` holds active, planned, and historical litters.
- `content/shows/` holds dog show appearances and result notes.
- `content/services/` holds the kennel's service categories.

This is intentionally a scaffold, not a fake promise. The public homepage is still hand-authored in `index.html`, but the repo is now structured so the next step can be a real content-driven frontend instead of more hardcoded HTML.

Production note:

- `admin/config.yml` is set up for GitHub-backed editing of `Argos-odysseus/fidel-puddel-showcase`.
- To use `/admin/` on a live GitHub Pages site, the project still needs a working auth path for Decap CMS. `local_backend: true` is included for local editing during development.

Archive source:

- Primary snapshot: https://web.archive.org/web/20240420101610/https://www.fidel-puddel.net/
- CDX inventory saved in `archive/cdx-all.json` and `archive/cdx-www-all.json`.
- Primary landing page saved in `archive/wayback-20240420.html`.
- Menu extraction saved in `archive/menu-urls.tsv`.
- A small subset of fetched HTML pages is saved in `archive/pages/`.

## Recoverable content

The 2024 landing snapshot exposed a large One.com-generated site menu with 69 internal menu links. The CDX index returned 735 archived 200-status captures for the domain, including 365 HTML entries and 231 image entries.

Recovered high-level structure:

- Forside / landing page.
- Oversikt / news overview.
- Om oss / About Us.
- Hundeklipp.
- Dog Shows, Puppy Shows, Breeding Classes.
- Til salgs / For Sale and New litters.
- Avlshanner / Studs.
- Poodle of the Year.
- Våre hunder with dog pages for Bowie, Karri, Janko, Kaffe, Zanzibar, Kamfer, Sioux, Nona, Arizona, Almeria and others.
- Veteran pages.
- Opphav / Origin and exports.
- Champions and list of champions.
- Stamtavle / Pedigree and Bevegelse / Movement.
- Memoriam pages.
- Kontakt and map.
- Guestbook pages 1-15.
- Linker / recommended links.

Specific content used in the modern site:

- Kennel/business name: Kennel Fidel.
- Archive tagline/highlight: "Kennel Fidel - 118 Champions".
- Operators: Eva Nygård and Gro Staurheim.
- Background: Eva Nygård had been active with poodles for over 50 years through breeding, shows and grooming; Gro Staurheim had been involved with the poodles for 34 years.
- Contact channels from archive: `fidelpuddel@gmail.com`, `997 41 311`, `grstau@online.no`, `952 82 035`.
- Last archived litter: medium poodles born 21.03.2023, one black female and two apricot males, after NUCH Fidel Arizona and Tixobambixo's Helmer of Ther-Lia.
- Puppy philosophy: sell to suitable homes that meet poodle exercise and grooming needs; breeder helps with grooming, clipping and show guidance; puppies were described as health checked, environmentally trained and used to car trips in a crate.
- Dog examples: Fidel Face Of A Devil "Bowie", Fidella Starface "Karri", Tixobambixo Khamfer Of El-Zanz, Fidel Zanzibar, Fidel Arizona, Fidel Winona.
- Results/highlights: Toy of the Year 2018/2019/2020, Crufts qualification, BOB/BIS/SAR references, and extensive champion history.
- News flow examples from the overview/show pages: Sandefjord 27.11.2022, NPK Hokksund 27.08.2022, the archived 2023 litter note, and the planned Winona/Peter Pan litter note.

## Recovered assets and limitations

The archive listed many image URLs, including One.com `____impro/1/onewebmedia/...` images. Three usable archived dog/show photos were recovered and are used in the page:

- `assets/photos/archive-dog-02.jpg`
- `assets/photos/archive-dog-03.jpg`
- `assets/photos/archive-dog-04.jpg`

One larger archived image partially downloaded as corrupt/gray content and is not included in the published repo. Many other images were present in CDX but were not practical to recover within this bounded run because Wayback binary retrieval was slow and intermittently returned timeouts or partial content.

No missing data has been fabricated. Where data may be outdated, the live page avoids presenting it as current availability and keeps the confirmation caveat subtle in the footer/contact framing.

## Field research

Research sources used:

- NKK ethical rules for breeding: https://www.nkk.no/registrering/etiske-grunnregler-og-avlsstrategi/etiske-grunnregler/
- Norsk Puddelklubb breeding recommendations: https://puddelklubb.no/avl-og-oppdrett/avlsanbefalinger/
- Mattilsynet dog breeding guidance: https://www.mattilsynet.no/dyr/kjaeledyr/hund/hundeavl
- Mattilsynet dog ownership/buyer guidance: https://www.mattilsynet.no/dyr/kjaeledyr/hund/veiledning-om-hold-av-hund
- NKK registration restrictions overview: https://www.nkk.no/registrering/raser-med-krav-for-registrering/
- NKK health resources: https://www.nkk.no/helse/
- If guide to choosing a serious breeder: https://www.if.no/magasinet/hund/kjope-hund/velg-riktig-oppdretter

Design implications:

- Make health, temperament, documented testing, registration and buyer expectations easy to find.
- Do not present old litters as currently available.
- Use clear puppy inquiry guidance instead of a generic contact form.
- Avoid overexposing private home addresses on a public static site; the demo keeps phone and email prominent and only uses regional location labels.
- Include static equivalents for dynamic/archive-only features such as guestbook and map.
- Present the site as a living kennel/blog front page rather than an archive exhibit, while keeping provenance in README/footer.

## Feature mapping

- Original large side menu -> top navigation with `Hjem`, `Nyheter`, `Våre hunder`, `Valper`, `Meritter`, `Om`, and `Kontakt`.
- Original `Oversikt`, `Dog Shows`, `Puppy Shows`, `Til salgs`, and `New litters` -> a news-led homepage with featured stories and dated update cards.
- Original dog pages, studs, veterans, and champions -> profile cards and merit blocks on the homepage.
- Original `Hundeklipp` page -> folded into the about/news sections as part of the kennel identity.
- Original contact pages -> static contact cards and inquiry guidance, without a fake backend form.
- Recovered archive photos -> reused as hero, feature-story, dog-profile, and gallery imagery instead of being isolated as archive evidence.

## Verification

Completed local gates:

- HTML parsed with Python `html.parser`.
- Local link and asset references checked from `index.html`.
- Recovered image bytes checked with `file`; three usable JPEGs are referenced by the page.
- `git diff --check -- fidel-puddel-showcase` passed.
- Local HTTP server returned `200 OK` from `http://127.0.0.1:8877/`.
- Browser screenshots captured at desktop and mobile sizes.
- Screenshot inspection checked for blank page, clipped text, overlapping text and broken layout.
- Rendered-text sanity check should confirm the blog-style surface text such as `Kennel Fidel`, `Utvalgte innlegg`, `Fidel Face Of A Devil`, and `Kontakt`.

Limitations:

- The local system `tidy` binary is too old for HTML5 semantic tags and reports false errors for `header`, `nav`, `main` and `section`.
- Wayback image binaries were only partially recoverable; three generic archive photos are used, and unmatched dog cards keep placeholders.
