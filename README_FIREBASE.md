# Firebase Hosting + GitHub synchronization

Project ID: `zahranicni-sazkove-kancelare`

Live default domains after Hosting is enabled:

- `https://zahranicni-sazkove-kancelare.web.app/`
- `https://zahranicni-sazkove-kancelare.firebaseapp.com/`

The site uses `https://zahranicni-sazkove-kancelare.web.app/` as the canonical SEO URL. Both Firebase domains serve the same Hosting release.

## Repository layout

- `public/` - everything Firebase Hosting publishes.
- `firebase.json` - Hosting configuration.
- `.firebaserc` - Firebase project binding.
- `.github/workflows/firebase-hosting-deploy.yml` - automatic live deployment on every push to `main`.

## One-time setup

1. Create/select the Firebase project with Project ID `zahranicni-sazkove-kancelare` and enable **Firebase Hosting**.
2. In Firebase Console open **Project settings -> Service accounts** and generate a private JSON key for a service account that can deploy Hosting.
3. In the GitHub repository open **Settings -> Secrets and variables -> Actions -> New repository secret**.
4. Create the secret exactly as:

   `FIREBASE_SERVICE_ACCOUNT_ZAHRANICNI_SAZKOVE_KANCELARE`

   Paste the complete JSON key as its value.
5. Push this repository to the `main` branch. The GitHub Action will deploy `public/` to the live Firebase Hosting channel.

After that, GitHub is the source of truth: every push to `main` publishes the current `public/` snapshot. Changed files are updated and deleted files disappear from the next Firebase release.

## Manual deploy if needed

```bash
npx firebase-tools deploy --only hosting --project zahranicni-sazkove-kancelare
```

## Local preview

```bash
npx firebase-tools serve --only hosting --project zahranicni-sazkove-kancelare
```

## Affiliate data

The affiliate table loads dynamically from:

`https://777cdnfiles.site/data/fc6a0c83e52b56b5.php`
