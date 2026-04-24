# Handoff: Wisdom Surgery Clinic — New Patient Registration Form

## Overview
A fully interactive, multi-step new patient registration form for Wisdom Surgery Clinic (wisdomsurgery.clinic), an Australian Oral & Maxillofacial Surgery specialist practice. The form collects all standard information required for a new patient at an Australian specialist surgical clinic, including Medicare/DVA details, health history, emergency contacts, referral details, and consent with a drawn signature.

## About the Design Files
The files in this bundle are **high-fidelity design references built in HTML/React** — they show exactly how the form should look and behave, but are prototypes, not production code. Your task is to **recreate this form in the existing website's environment**, matching the visual design and interactions as closely as possible using whatever stack the site runs on (plain HTML/CSS/JS, or a framework if present).

## Fidelity
**High-fidelity.** The prototype is pixel-accurate with final colours, typography, spacing, interactions, and copy. Recreate it as closely as possible. The bundled HTML file (`New Patient Registration Bundled.html`) can be opened in any browser for reference.

---

## Form Structure — 5 Steps

### Step 1 — Patient Personal Details
Fields: Title (radio pills), Surname, Given Names, Preferred Name, Date of Birth, Country of Birth, Gender (radio), Residential Address, Suburb, State (select), Postcode, Postal Address (if different), Mobile, Home/Work Phone, Email, Occupation, Language Spoken at Home, Interpreter Required (radio), Marital Status (radio), Indigenous status (radio)

### Step 2 — Medicare & Health Funding
Fields: Medicare Card Number, Reference Number, Expiry, Pension/Health Care Card Number + Expiry, DVA Card Number + Type, Private Health Insurance Fund Name, Membership Number, Policy Number, Cover Type

### Step 3 — Emergency Contact & Referral
Fields: Contact Name, Relationship (select), Mobile, Alternative Phone
Referral notice (see copy below), then: Referring Doctor/Dentist Name, Practice Name, Phone, Fax/Email, Reason for Referral (textarea)

**Referral notice copy:**
> As a specialist practice, we generally require a referral. **If your referral has already been sent to us, please disregard this section.** If you still need to arrange a referral, please provide your referring practitioner's details below.

### Step 4 — Health History
Fields: Usual GP/Medical Centre, Allergy status (radio + conditional list textarea), Current Medications (textarea), Blood thinners checklist (with warning flag if selected), Medical conditions checklist (23 conditions), Other medical history (textarea), Previous anaesthetic (radio), Anaesthetic reaction (radio + conditional detail), Previous oral/jaw surgery (radio + conditional detail), Smoking (radio), Alcohol (radio), Pregnancy status (radio)

### Step 5 — Consent & Signature
Four consent blocks, each with title, body text, and an individual agree checkbox:
1. Privacy Policy & Information Collection
2. My Health Record
3. Communication Consent
4. Accuracy of Information

Then: Patient Full Name (text input), Date (auto-filled, read-only), drawn Signature (canvas pad)

---

## Interactions & Behaviour

- **Multi-step navigation** with Back / Continue / Submit buttons
- **Progress indicator** — 5 numbered dots at the top, clickable to jump to any step
- **Step-level validation** on Continue — required fields highlighted with red border + error message; page scrolls to top on error
- **Conditional fields** — allergy list shows only if "Yes — I have allergies" selected; anaesthetic detail shows if reaction selected; oral surgery detail shows if "Yes" selected
- **Blood thinner warning** — an amber warning banner appears below the checklist if any item is selected
- **Signature pad** — HTML5 canvas, mouse and touch support, Clear button, placeholder text when empty
- **Success screen** — replaces form on submit, shows patient's first name and email
- **All consent items must be agreed** before submission is allowed

## Validation Rules
- Step 1 required: Title, Surname, Given Names, DOB, Address, Suburb, Postcode, Mobile, Email (+ email format check)
- Step 2: no required fields
- Step 3 required: Emergency Contact Name, Relationship, Mobile (referral fields are optional)
- Step 4: no required fields
- Step 5 required: all 4 consents agreed, printed name, drawn signature

---

## Design Tokens

### Colours
| Token | Hex | Usage |
|---|---|---|
| Navy | `#152d4a` | Card headers background, body text |
| Teal | `#00b4cc` | Primary accent, buttons, progress dots, borders |
| Teal Dark | `#0091a8` | Button hover, subheadings |
| Teal Light | `#e0f7fa` | Card header background, pill selected bg, alert boxes |
| Teal Mid | `#80d8e8` | Borders on teal-light elements |
| Cream | `oklch(98% 0.006 210)` | Page background |
| Charcoal | `#1e3346` | Body text |
| Mid | `#4d6b80` | Labels, secondary text |
| Muted | `#8aaabb` | Placeholders, helper text |
| Border | `#d0e4ec` | Input borders, dividers |
| Error | `#c0392b` | Validation errors |

### Typography
- **Font:** DM Sans (Google Fonts) — weights 300, 400, 500, 600
- **Body:** 14px / 1.55 line-height
- **Labels:** 10.5px, 600 weight, 0.8px letter-spacing, uppercase
- **Section title:** 20px, 500 weight
- **Step labels:** 10.5px

### Spacing
- Card padding: 30px 36px
- Field gap: 18px
- Section divider margin: 22px top/bottom

### Borders & Radius
- Input border: 1.5px solid `#d0e4ec`, radius 8px
- Card radius: 14px
- Pill radius: 7px
- Button radius: 9px

### Shadows
- Card: `0 2px 24px rgba(26,46,59,0.07)`
- Primary button: `0 2px 14px rgba(0,180,204,0.28)`

---

## Assets
| File | Usage |
|---|---|
| `uploads/WisdomSurgery_Logo_Horizontal.png` | Page header (white bar, top of page) |
| `uploads/WisdomSurgery_Logo_Circle.PNG` | Small circle logo in each form card header (top-right, 54×54px) |

Logo colours: deep navy `#152d4a`, teal-to-cyan gradient. Always display on white or very light backgrounds.

---

## Files
- `New Patient Registration.html` — main editable source file (React/Babel inline)
- `New Patient Registration Bundled.html` — self-contained single file (logos embedded), good for standalone sharing
- `uploads/` — logo assets

---

## Notes for Implementation
- The form does not currently POST data anywhere — on submit it shows a success screen. You will need to wire up form submission to a backend endpoint or form service (e.g. Netlify Forms, Formspree, or a custom endpoint).
- The signature is captured as a base64 PNG data URL from an HTML5 canvas — this can be sent as part of the form payload or saved server-side.
- The drawn signature pad requires `touch-action: none` on the canvas element for correct mobile behaviour.
- For accessibility, ensure all radio/checkbox inputs have associated labels in the final implementation.
