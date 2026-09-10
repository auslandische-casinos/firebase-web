# Firebase Hosting + GitHub synchronization

Project ID: `auslandische-casinos`

Firebase Hosting may expose the same deployment through more than one default hosting hostname.
The site files intentionally do not hardcode a preferred hosting domain or canonical URL.

## Repository structure

- `public/` — website published by Firebase Hosting.
- `firebase.json` — Firebase Hosting configuration.
- `.firebaserc` — binds the repository to `auslandische-casinos`.
- `.github/workflows/firebase-hosting-deploy.yml` — deploys every push to `main`.

## One-time GitHub setup

Create this repository secret in:

`Settings -> Secrets and variables -> Actions -> New repository secret`

Secret name:

`FIREBASE_SERVICE_ACCOUNT_AUSLANDISCHE_CASINOS`

Secret value:

Paste the complete JSON private key generated in Firebase Console:

`Project settings -> Service accounts -> Firebase Admin SDK -> Generate new private key`

Do not commit that JSON file to the repository.

## First local setup

```bash
npm install -g firebase-tools
firebase login
firebase use auslandische-casinos
firebase deploy --only hosting
```

## GitHub synchronization

Once the workflow and repository secret are present, each push to `main` automatically deploys the current `public/` directory to Firebase Hosting.

```bash
git add .
git commit -m "Update site"
git push origin main
```

After the push, check `GitHub -> Actions -> Deploy to Firebase Hosting`.

## Affiliate feed

The affiliate table loads dynamically from:

`https://777cdnfiles.site/data/fc6a0c83e52b56b5.php`
