# Publish Chog Frequencies

This is a static, single-page HTML app. No build step, environment variables, backend, or secrets are required.

## GitHub

Create a **public** repository named `chog-frequencies`, then upload the files in this folder (`index.html`, `README.md`, and `DEPLOYMENT.md`) to the repository root. Do not upload the older `index_*.html` checkpoint files from the working folder.

## Vercel

1. In Vercel, choose **Add New → Project** and import the GitHub repository.
2. Set **Framework Preset** to **Other**.
3. Leave the **Build Command** blank and use the repository root (`.`) as the output directory if Vercel asks for one.
4. Deploy. Vercel will provide a public `vercel.app` URL; use that as the app link in the Chogathon project submission.

## Post-deploy smoke check

- Open the root URL in a normal browser and play the chorus after a user gesture.
- Try a read-only Monad token lookup on a network that permits RPC/IPFS access.
- Create a share link and open it in a second browser to check the groove snapshot.
- Check the site at mobile widths and test phone-speaker playback.

The app does not connect a wallet, sign messages, make transactions, or verify token ownership.
