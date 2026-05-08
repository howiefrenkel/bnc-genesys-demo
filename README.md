# Genesys Cloud Demo for BNC

This is a static, GitHub Pages-ready demo site for hosting a Genesys Cloud Messenger deployment.

## Files

- `index.html` - the complete single-page demo site
- `.nojekyll` - prevents GitHub Pages from running Jekyll processing
- `.gitignore` - basic local development exclusions

## Deploy to GitHub Pages

1. Create a new GitHub repository.
2. Upload these files to the root of the repository.
3. Commit the files to the `main` branch.
4. Go to **Settings > Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**.
6. Select branch `main` and folder `/root`.
7. Save.

Your site will be published at a URL similar to:

```text
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
```

## Genesys Cloud Messenger notes

The Genesys Cloud Messenger snippet is already included in the `<head>` of `index.html`.

If Messenger does not appear after publishing:

1. Confirm the Messenger deployment is active.
2. Confirm the deployment is assigned to the correct Messenger configuration.
3. Confirm the configuration has been published.
4. Confirm an inbound message flow is assigned and published.
5. If domain restrictions are enabled, add the GitHub Pages URL to the allowed domains.
6. Test browser language preferences if you expect localized Messenger labels.


## Assets

The site includes `assets/genesys-logo.png`, the Genesys logo used throughout the page. Keep the `assets` folder with `index.html` when uploading to GitHub.

## Browser language detection for Architect flow language

The page now detects the visitor browser language with `navigator.languages` and writes these Messenger custom attributes through `Database.set`:

- `browserLanguage` - the primary browser language, for example `fr-CA` or `en-US`
- `browserLanguages` - the full browser language list as a comma-separated string
- `flowLanguage` - normalized for Architect, currently either `fr-CA` or `en-US`
- `preferredLanguage` - same value as `flowLanguage`

In Genesys Cloud Architect, add a **Get Participant Data** action at the start of the inbound message flow and read the exact attribute name:

```text
flowLanguage
```

Store it in a string variable such as `Flow.BrowserLanguage`, then use a Decision action:

```text
Flow.BrowserLanguage == "fr-CA"
```

On the True branch, use **Set Language = French Canada (fr-CA)**. On the False branch, use **Set Language = English United States (en-US)**. Then continue to your bot flow or routing logic.
