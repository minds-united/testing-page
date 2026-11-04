# testing-page (MyDigital ID opener)

One static page: opens the MyDigital ID app for a login started on another device, because Telegram can't link
to the app (`misignet://`) directly. The road tax bot sends `https://minds-united.github.io/testing-page/#<login id>`.

- The login id is after `#`, which browsers never send to the server.
- It asks for the NRIC first and opens the app only if it matches a salted, slow (PBKDF2) fingerprint in the
  link (the NRIC itself is never in the link or the page). 3 wrong tries lock it.
- It only opens MyDigital ID logins for `sso.digital-id.my`, exactly like that login page's own phone button.
- No outside files, no tracking, nothing sent anywhere.  The app still asks for the owner's PIN.
- Only the person whose NRIC is on the Telegram message may approve.

Source of truth: `rt-renewal-scraper/opener/index.html` (private repo).
