---
title: "Test Page"
date: 2026-01-18
draft: false
---

# Test Page

This page is for testing and isn't in the menu. Access it directly at `/test/`.

---

## Formspree Form Test

Below is a Formspree form styled to match the theme:

<style>
.contact-form .form-control {
    background-color: var(--secondary-color);
    color: var(--text-color);
    border-radius: .7rem;
    border: 1px solid var(--text-secondary-color);
    box-shadow: 0px 8px 56px rgb(15 80 100 / 5%);
}
.contact-form .btn {
    border-radius: .5rem;
    border-color: var(--primary-color);
    background-color: var(--secondary-color);
}
.contact-form .btn:hover {
    opacity: .7;
}
</style>

<div class="contact-form">
    <div class="row justify-content-center">
        <form action="https://formspree.io/f/xlggjzpd" method="POST" class="col-md-7">
            <div class="form-group pt-3">
                <input type="text" class="form-control" name="name" required placeholder="Your name">
            </div>
            <div class="form-group pt-3">
                <input type="email" class="form-control" name="email" required placeholder="Your email">
            </div>
            <div class="form-group pt-3">
                <textarea class="form-control" name="message" required placeholder="Your message" rows="5"></textarea>
		    <p class="fs-description">What would you like to discuss?</p>
            </div>
            <div class="form-group text-center pt-3">
                <button type="submit" class="btn">Send Message</button>
            </div>
        </form>
    </div>
</div>

---

## Notes

- Uses Bootstrap classes from the theme (`form-control`, `btn`, `form-group`)
- The `col-md-7` and `justify-content-center` center and constrain the width
- Matches the homepage contact form styling
