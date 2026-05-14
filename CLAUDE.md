# Wisdom Surgery Clinic — Public Patient Site

## What this is
Public patient-facing website for Dr Anna Raymond's Oral & Maxillofacial Surgery practice.
Lives at **anna-bryan-joys.github.io/wisdomsurgery** (GitHub Pages, no custom domain).
Separate from the staff portal (wisdomsurgery.team).

## Stack
- Vanilla HTML/CSS/JS, no framework, no build step
- Tailwind CSS (CDN), Google Fonts (Playfair Display + DM Sans)
- Navy/teal color palette — match existing design when adding anything
- Deployed via `git push`

## File map
```
index.html                    # Main public homepage (65KB — grep don't read whole file)
new-patient-registration.html # New patient intake form (92KB — grep only)
welcome.html                  # Welcome/intro page
referrers.html                # Referring doctor directory
payment.html                  # Payment info
staff-schedule.html           # Schedule view (may be redundant with staff portal)
letterhead-navy-gold.html / letterhead-teal.html  # Letterhead templates
new-patient-form/             # Folder with patient form assets/uploads
brand_assets/                 # Logos and images — don't read
```

## Critical rules
- **Never read whole HTML files** — 30KB–92KB monoliths with embedded CSS+JS. Grep for what you need.
- No build step — changes go live on push, test in browser before pushing
- This is patient-facing — keep tone professional and accessible
