# yuserlab.co: landing page

Static site for GitHub Pages: one `index.html` with inline CSS/JS, plus `assets/`.

```
index.html
CNAME                  → yuserlab.co (custom domain)
assets/grace-coelho.jpg | .webp
assets/og-image.jpg    → link preview (WhatsApp, LinkedIn)
```

## Configuration

Everything lives in the `CONFIG` block at the start of the `<script>` in `index.html`:

| Key | What it does |
|---|---|
| `endpoints.international` / `br_companies` / `participants` | URL each form posts to (e.g. Formspree). `null` = form shows "not connected" and sends nothing. |
| `contactEmail` | Address shown in the privacy notice. |
| `umamiWebsiteId` | Umami Cloud Website ID. `null` = no analytics. |
| `analyticsDomain` | Analytics only load on this domain, so local tests aren't counted. |

## Analytics events (Umami)

Umami counts pageviews, referrers, countries, devices and UTM parameters automatically. Custom events:

| Event | When | Properties |
|---|---|---|
| `choose_path` | Click on one of the 3 audience cards | `audience` |
| `nav_click` | Click on a top-bar link | `audience` |
| `entry_link` | Visitor arrives on a journey link (`/#international`, `/#empresas`, `/#participar`) | `target` |
| `section_view` | Section seen (once per visit) | `section` |
| `form_cta_click` / `form_open` | Journey form button clicked / form opened | `audience` |
| `form_start` | First field focused | `audience` |
| `form_error` | Submit with missing/invalid fields | `audience`, `fields` (field names only) |
| `form_complete` | Valid submit | `audience`, `support` / `stage` / `whatsapp` / `timeline` (choices only, no personal data) |
| `form_sent` / `form_send_failed` / `form_not_connected` | Result of sending | `audience` |
| `contact_menu_open`, `email_provider`, `email_copy` | Contact box | `provider` |
| `linkedin_click` | LinkedIn links | `location` |
| `pt_bio_open` | Portuguese bio opened | – |
| `footer_click` | Footer contact link | `location` |

No names, emails, companies or free-text answers are ever sent to analytics.
