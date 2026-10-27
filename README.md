# Ölkalendern – GitHub Pages

## GitHub settings

Under **Settings → Secrets and variables → Actions**, add these repository variables:
- `FB_API_KEY`
- `FB_AUTH_DOMAIN`
- `FB_PROJECT_ID`
- `FB_APP_ID`

Add this repository secret:
- `ADMIN_PW`

The GitHub Actions workflow substitutes these values into `index.html` before deployment.

## Important security note

`ADMIN_PW` is injected into a public HTML/JavaScript file and can be read by visitors. A GitHub Secret protects the value while stored in GitHub, but does not keep it secret after it is embedded in the deployed page. Do not rely on this client-side password to protect sensitive operations. Use Firebase Authentication and restrictive Firestore Security Rules for real access control.

Firebase web configuration values are normally visible to users. Protect your Firestore data with Security Rules and configure Firebase API-key restrictions where appropriate.

## Deploy

1. Upload `index.html` to the root of the repository.
2. Upload `.github/workflows/deploy.yml` at that exact path.
3. Add the variables and secret listed above.
4. In **Settings → Pages**, select **GitHub Actions** as the build and deployment source.
5. Commit/push to `main` or run the workflow manually from **Actions**.
