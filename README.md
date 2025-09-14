# Broken Authentication Attacks (OWASP)

This repository explains and demonstrates broken authentication attacks based on the OWASP Top 10, including *Session Hijacking, **Session Fixation, and **Brute Force Attack*. Each section includes a description, the typical attack flow following OWASP guidelines, and mitigation strategies.

---

## Session Hijacking

*Description:*  
Session hijacking occurs when an attacker steals or predicts a user’s session token (usually from cookies or URL parameters) to take control of an authenticated session.

*OWASP Attack Flow:*  
1. Attacker captures session token via network sniffing, Cross-Site Scripting (XSS), or insecure cookies.
2. Attacker sends the stolen token with their own request.
3. The server sees the token as valid and authorizes the attacker as the victim.

*Mitigation:*  
- Use secure (HTTPS-only) cookies.
- Set cookies with HttpOnly and Secure flags.
- Regenerate session IDs on login.
- Implement short session timeouts and logout functions.

---

## Session Fixation

*Description:*  
Session fixation attacks trick users into authenticating with a session ID provided by the attacker, letting the attacker use the same session ID after login.

*OWASP Attack Flow:*  
1. Attacker supplies a known session ID to the victim, often by embedding it in a URL.
2. Victim logs in; authenticated status is linked to attacker-controlled session ID.
3. Attacker uses the same session ID to access the victim’s account.

*Mitigation:*  
- Always generate a new session ID after successful login.
- Prevent session ID tampering via URLs.
- Invalidate old or unused session IDs.

---

## Brute Force Attack

*Description:*  
Brute force attacks rapidly guess passwords using automation until the correct credentials are found.

*OWASP Attack Flow:*  
1. Attacker automates repeated login attempts using various password combinations.
2. If the application does not have rate limiting, CAPTCHA, or account lockouts, attacker eventually guesses correct password.
3. Attacker gains unauthorized user access.

*Mitigation:*  
- Enforce strong password policies.
- Use account lockout or delay mechanisms.
- Implement CAPTCHAs on authentication forms.
- Monitor and alert on abnormal login attempts.

---

## Disclaimer

This repository is for *educational and authorized testing only*. Never use these attack methods on systems without explicit permission.

## References

- [OWASP Top 10: Broken Authentication](https://owasp.org/www-project-top-ten/2017/A2_2017-Broken_Authentication)
-Learnt from tryhackme rooms

