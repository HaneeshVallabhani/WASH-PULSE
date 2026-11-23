# Deploy WashPulse to Netlify

WashPulse is a static HTML site. Netlify does not need to run a build command; the root `netlify.toml` already sets `publish = "."`.

## Connect GitHub once

1. Sign in to Netlify: <https://app.netlify.com/>
2. From your team dashboard, choose **Add new project → Import an existing project**.
3. Select **GitHub** and authorize Netlify when prompted.
4. Choose repository **HaneeshVallabhani/Haneesh_3579**.
5. Keep the production branch as `main`. Confirm the publish directory is `.` and the build command is blank (the checked-in `netlify.toml` sets these values).
6. Select **Deploy** / **Publish**.

Netlify will create the site and deploy it. After this one-time connection, each push to `main` automatically triggers a new deployment. You do not need a Netlify API token or GitHub Actions secrets for this native integration.

## Updating the site

Commit or push changed files to the repository's `main` branch. Netlify automatically builds and publishes the update. Check the site's **Deploys** page to see deployment status and the live URL.

## Current demo limitations

- Student and staff records are saved in browser `localStorage` and synchronized with `BroadcastChannel` only within the same browser context. Different devices do not share data.
- `SMS_API_ENDPOINT` is empty. The current OTP screen does not send a real SMS or validate a server-issued OTP; any four digits pass the front-end check.
- The generated QR graphic is a visual placeholder, not a standards-compliant camera-scannable QR code. The staff screen currently accepts typed student or bag IDs.

Netlify hosting makes the static demo publicly reachable; it does not add backend storage, real SMS delivery, secure authentication, or cross-device synchronization. Those require a backend and service integration.
