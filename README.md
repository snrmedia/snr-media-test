# SNR Media Deploy Test

Tiny static project for testing automatic deployment to:

```text
https://snr-media.com/test/
```

Deployment target folder must exist on the hosting account.

## What You Need

1. A GitHub repository containing these files.
2. An FTP account from tarhely.eu/cPanel.
3. These GitHub repository secrets:

```text
FTP_SERVER
FTP_USERNAME
FTP_PASSWORD
```

The FTP account should be restricted to:

```text
/public_html/test/
```

The deploy workflow uploads into the FTP account's root:

```text
/
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

This setup assumes the FTP account is already restricted to the target folder.
For another project, create another FTP account restricted to that project's
folder, for example:

```text
/public_html/another-project/
```

Keep the workflow upload path as:

```yaml
server-dir: /
```

Then the site would be available at:

```text
https://snr-media.com/another-project/
```
# snr-media-test
