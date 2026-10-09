# Cruxy Digital website

A single-page, no-build static site (HTML + CSS + vanilla JS). No framework, no npm install,
no CMS. Copy and images are edited directly in the files below.

## How it's structured

```
index.html            ← the whole site (header, hero, services, CTA, contact form, footer)
css/style.css          ← styles + self-hosted Poppins @font-face declarations
js/site.js              ← footer year + the contact-form submission
fonts/                  ← self-hosted Poppins woff2 files (no Google Fonts dependency)
images/cruxy-logo.svg, cruxy-mark.svg   ← brand logo (header/footer) and favicon mark
images/hero-photo-PLACEHOLDER.jpg        ← swap this for a real hero photo
images/logos/                            ← Shopify / Klaviyo / Google Analytics logos shown in the services section
```

## Contact form → email

The form in `#contact` posts to the `agency-contact-form` Supabase edge function (source in the
`cruxy-time-tracker` repo, `supabase/functions/agency-contact-form`), which emails the submission to
Cory through Resend. Replies go straight to the visitor (reply-to). Nothing is sent to Klaviyo. The
function only accepts requests from cruxydigital.com, this project's Vercel previews and localhost.
On success the form is swapped for a "Thanks! We'll be in touch soon." confirmation.

## Hosting — Vercel

Deployed on Vercel (project `agency-website`), connected to this repo. A push to a branch gets a
preview URL; a push to `main` publishes to production. The production domain is cruxydigital.com.
