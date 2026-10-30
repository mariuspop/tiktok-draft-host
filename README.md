# tiktok-draft-host

Template for the public static site that `scripts/push-tiktok-drafts.sh` needs: copy these files into a new **public GitHub repo** of your own (any name; `tiktok-draft-host` matches the script's default), enable GitHub Pages on its main branch, and clone it to `~/github/tiktok-draft-host`. Then, in the TikTok developer portal (Manage apps → your app):

- **URL properties:** verify the Pages URL by URL prefix (download the signature file they give you, commit it to the repo root, push, verify).
- **Login Kit → Redirect URI:** `https://<you>.github.io/tiktok-draft-host/callback.html`
- **Terms of Service / Privacy Policy URLs:** `https://<you>.github.io/tiktok-draft-host/#terms` and `…/#privacy`
- **Products:** Login Kit + Content Posting API (the upload / inbox flow needs scope `video.upload`).

Put the app's key, secret and redirect URI in `~/.tiktok/client.json`, set `HOST_BASE_URL` in the script's CONFIG block, and run `scripts/push-tiktok-drafts.sh glinded --login`.

`renders/` is where the script parks each pushed photo for the minute TikTok needs to fetch it; it deletes them afterwards.
