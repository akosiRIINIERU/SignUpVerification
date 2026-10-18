# Random Client authentication landing page

This GitHub Pages site handles Supabase email-confirmation links and password-recovery links. It no longer asks users to manually enter a signup OTP.

## Supabase configuration

1. In Supabase Dashboard → Authentication → URL Configuration, add `https://akosiriinieru.github.io/SignUpVerification/` to the allowed redirect URLs.
2. For password recovery, set the app's `resetPasswordForEmail` `redirectTo` to `https://akosiriinieru.github.io/SignUpVerification/`. This page also accepts recovery links that return `type=recovery` and tokens in the URL hash.
3. Keep the email confirmation template using the Supabase confirmation URL (`{{ .ConfirmationURL }}`) or the configured PKCE redirect pattern appropriate for the project.
4. The page uses the public anon key only. Never put a Supabase service-role key in this repository.
5. After updating the site, test with a newly requested reset link. Links are single-use and expire; previously shared links should not be reused.

## Important

GitHub Pages only serves the static frontend. The password change is performed by Supabase Auth after the recovery session is established.
