# Security policy

Lectern reads the login for one website from a browser on the user's own computer. We take any problem in that area seriously.

## Report a problem privately

Do not open a public issue for a security problem.

1. Go to the repository where you found the problem, for example [lectern-cookie-reader](https://github.com/Lectern-HQ/lectern-cookie-reader).
2. Open the **Security** tab and click **Report a vulnerability**.
3. Describe:
   - what you found, and which version or commit;
   - the steps to reproduce it;
   - what an attacker could do with it.

Only the maintainers can see the report. We answer within 7 days, keep you informed while we fix it, and credit you in the release notes if you want.

## In scope

- Reading cookies for any website other than the one the user asked for.
- Cookie values, keys or passwords appearing in logs, error messages, crash reports or files that are not deleted.
- Any data leaving the user's computer other than the licence check.
- Bypassing a browser's or the operating system's protection (Keychain prompt, app-bound encryption, file permissions).
- Problems in how updates, models or bundled tools are downloaded and verified.

## Out of scope

- Problems that need someone who already controls the user's account on the computer.
- Missing security headers or similar findings on the marketing website, unless they lead to real harm.

## Supported versions

Only the latest release of each project receives security fixes.
