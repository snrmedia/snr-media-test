# SNR Media Deploy Test

Tiny static project for testing automatic deployment to:

```text
https://snr-media.com/test/
```

## What You Need

1. A GitHub repository containing these files.
2. An FTP account from tarhely.eu/cPanel.
3. These GitHub repository secrets:

```text
FTP_SERVER
FTP_USERNAME
FTP_PASSWORD
```

The deploy workflow uploads the repository files to:

```text
/public_html/test/
```

If your FTP account opens directly inside `public_html`, change the workflow path
to:

```text
/test/
```

## Setup

Create a new GitHub repository, then push this folder:

```bash
git init
git add .
git commit -m "Add deploy test page"
git branch -M main
git remote add origin git@github.com:YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

Then add the FTP secrets in GitHub:

```text
Repository Settings > Secrets and variables > Actions > New repository secret
```

After the next push to `main`, GitHub Actions will upload the page.

You can also trigger it manually from:

```text
GitHub > Actions > Deploy test page > Run workflow
```

## Changing The URL

To deploy somewhere else, edit `.github/workflows/deploy.yml`:

```yaml
server-dir: /public_html/another-project/
```

Then the site would be available at:

```text
https://snr-media.com/another-project/
```
# snr-media-test
