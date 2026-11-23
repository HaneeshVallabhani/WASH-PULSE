# Deploy WashPulse to Netlify

This is a static HTML site and does not need a build command.

## First deploy

1. Sign in to Netlify.
2. Open <https://app.netlify.com/drop>.
3. Drag the folder containing `index.html` and `netlify.toml` onto the page.
4. Netlify publishes the site and gives you a URL.

## Automatic deploys from GitHub

The included `.github/workflows/netlify-deploy.yml` runs on every push to `main` and can also be started manually from GitHub Actions.

1. Create/claim the Netlify site from the first-deploy step.
2. In Netlify, open **Site configuration → General → Site details** and copy the **Site ID**.
3. In Netlify, open **User settings → Applications → Personal access tokens** and create a token. Keep it private.
4. In GitHub, open **Settings → Secrets and variables → Actions → New repository secret**. Add `NETLIFY_AUTH_TOKEN` and `NETLIFY_SITE_ID`.
5. Push to `main`, or open **Actions → Deploy WashPulse to Netlify → Run workflow**.

Never put the Netlify token in `index.html`, commit it to the repository, or share it in chat.

## Current demo limitations

- Student and staff records live in browser `localStorage` and `BroadcastChannel`; different devices do not share data.
- `SMS_API_ENDPOINT` is empty. The current OTP UI does not send a real SMS or validate a server-issued OTP; any four digits pass the front-end check.
- The displayed QR graphic is a visual placeholder, not a standards-compliant camera-scannable QR code. The staff screen accepts typed student or bag IDs.

Netlify hosting makes the static demo publicly reachable; it does not add backend storage, SMS delivery, secure authentication, or cross-device synchronization. Those require backend and service integration.
