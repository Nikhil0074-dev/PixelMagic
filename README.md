#  PixelMagic — AI Magic Image Editor

A fully self-contained single-page HTML app for an AI-powered photo editing product. No build tools, no dependencies, no server required — just open `PixelMagic.html` in any modern browser.

---

##  Project Structure

```
PixelMagic.html   ← Complete app (HTML + CSS + JS in one file)
README.md         ← This file
```

---

##  How to Run

1. Download `PixelMagic.html`
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge)
3. That's it — no installation, no server needed

---

##  Pages

| Page | Description |
|---|---|
| **Main / Landing** | Hero section, features, AI enhancer demo, pricing |
| **Pricing** | Standalone pricing page with Free / Pro / Team plans |
| **Privacy Policy** | Full privacy policy (GDPR-aware) |
| **Terms of Service** | Full terms of service |
| **Contact** | Contact form + support email cards |

Navigation between pages is handled in JavaScript via `showPage(id)` — no actual page reloads occur.

---

##  Modals

| Modal ID | Purpose |
|---|---|
| `modal-signup` | Multi-step signup: form → OTP email verification → success |
| `modal-login` | Email + password login → success screen |
| `modal-reset` | Password reset: email → confirmation → new password form |
| `modal-bug` | Bug report form with category selector |

All modals can be opened via `openModal('modal-id')` and closed with `closeModal('modal-id')` or by clicking outside.

---

##  JavaScript Functions Reference

### Navigation
| Function | Description |
|---|---|
| `showPage(id)` | Switch to a page by element ID |
| `scrollToFeatures()` | Navigate to main page and scroll to `#features` |

### Modals
| Function | Description |
|---|---|
| `openModal(id)` | Open a modal overlay |
| `closeModal(id)` | Close a modal overlay |
| `closeModalOutside(event, id)` | Close modal when clicking the backdrop |
| `switchModal(from, to)` | Close one modal and open another |

### Toast Notifications
| Function | Description |
|---|---|
| `showToast(msg, duration?)` | Show a bottom-right toast message (default 3 s) |

### Forms & Validation
| Function | Description |
|---|---|
| `validateEmail(email)` | Returns `true` if the email format is valid |
| `showErr(el, msg, show?)` | Display or hide an error `<div>` with a message |
| `submitContact()` | Validates and "submits" the contact form |
| `submitBug()` | Validates and "submits" the bug report form |

### Auth Flows
| Function | Description |
|---|---|
| `doSignup()` | Validates the signup form, then shows OTP step |
| `verifyOTP()` | Checks the 6-digit OTP and advances to success |
| `resendOTP()` | Generates a new demo OTP and shows a toast |
| `doLogin()` | Validates login form and shows the success screen |
| `doReset()` | Validates email and advances the reset flow |
| `doNewPassword()` | Validates new password and shows the final reset step |

### Password Strength
| Function | Description |
|---|---|
| `getStrength(pw)` | Returns a score 0–4 based on length, uppercase, digits, symbols |
| `updateStrengthUI(barId, labelId, pw)` | Updates the coloured strength bar and label |
| `checkStrength(pw)` | Calls `updateStrengthUI` for the signup form |
| `checkStrengthNew(pw)` | Calls `updateStrengthUI` for the reset form |

### OTP Input
| Function | Description |
|---|---|
| `otpNext(el, idx)` | Auto-focuses next OTP box after a digit is typed |
| `otpBack(event, el, idx)` | Focuses the previous OTP box on Backspace |

### Scroll Animations
| Function | Description |
|---|---|
| `observeReveals()` | Uses `IntersectionObserver` to fade-in `.reveal` elements on scroll |

---


##  Design Tokens (CSS Variables)

```css
--blue:       #2563eb   /* Primary brand blue */
--blue-light: #3b82f6   /* Hover / lighter blue */
--blue-dark:  #1d4ed8   /* Active / darker blue */
--black:      #0a0a0f   /* Deep background */
--white:      #ffffff
--gray:       #6b7280   /* Body text secondary */
--gray-light: #f3f4f6   /* Backgrounds */
--gray-mid:   #e5e7eb   /* Borders */
--text:       #111827   /* Primary text */
--radius:     16px
--shadow:     0 4px 24px rgba(37,99,235,0.10)
```

---

##  Contact Emails

| Purpose | Address |
|---|---|
| General Support | support@pixelmagic.app |
| Bug Reports | bugs@pixelmagic.app |
| Billing | billing@pixelmagic.app |
| Partnerships | partners@pixelmagic.app |
| Legal & Privacy | legal@pixelmagic.app |

---

##  Demo Mode Notes

- **OTP verification** is simulated — the code is shown in a toast notification instead of being emailed. In production, replace `doSignup()` with a real API call.
- **Login** accepts any email + password of 5+ characters. Replace `doLogin()` with real authentication.
- **Contact and bug forms** show success UI but do not send data anywhere. Wire up a backend endpoint or a service like Formspree.
- **Password reset** is fully mocked (no actual email is sent).

---

##  Browser Support

Works in all modern browsers that support:
- CSS Grid & Flexbox
- `backdrop-filter`
- `IntersectionObserver`
- CSS Custom Properties
