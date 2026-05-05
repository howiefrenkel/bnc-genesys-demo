# BNC-style Genesys Cloud Messenger demo page

This is a static one-page demo site for hosting and testing a Genesys Cloud Messenger deployment.

> **DEMO ONLY:** This is not an official Banque Nationale website. It uses public visual references and links for demo/testing purposes only.

## Files

- `index.html` - the complete static demo webpage, including the Genesys Cloud Messenger snippet.
- `.nojekyll` - tells GitHub Pages not to process this as a Jekyll site.
- `.gitignore` - standard local/editor exclusions.

## Local preview

Open `index.html` in a browser, or run a local static server from this folder:

```bash
python3 -m http.server 8080
```

Then visit:

```text
http://localhost:8080
```

For the Genesys Messenger widget, testing from the final GitHub Pages HTTPS URL is recommended because Messenger deployments often depend on allowed domains and deployment configuration.

## Deploy with GitHub Pages

1. Create a new GitHub repository, for example `bnc-genesys-demo`.
2. Upload all files in this folder to the repository root.
3. Commit the files to the `main` branch.
4. In GitHub, go to **Settings > Pages**.
5. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
6. Set **Branch** to `main` and folder to `/root`.
7. Click **Save**.
8. GitHub Pages will publish the site at a URL like:

```text
https://YOUR-USERNAME.github.io/bnc-genesys-demo/
```

## Genesys Cloud Messenger checklist

If the Messenger does not pop up on GitHub Pages, check the Genesys Cloud deployment:

1. The Messenger deployment is active.
2. The deployment has a Messenger configuration assigned.
3. The configuration has the correct apps/features enabled, such as Messenger conversation.
4. An inbound Architect message flow is selected and published.
5. If domain restriction is enabled, add your GitHub Pages URL/domain to the allowed domains.
6. The deployment ID in `index.html` matches your Genesys Cloud deployment.

The demo page also includes a red **DEMO chat** button and a small Genesys status box to help diagnose whether the Messenger script loaded and whether the open command succeeded.
