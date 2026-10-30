# Jason Bohrer's website

A simple personal website for GitHub Pages, with a short bio and a publication list.
The site uses plain HTML and CSS, with no dependencies or build step.

## Write your bio

Open [index.html](index.html) and replace the introductory paragraph between the
`BIO START` and `BIO END` comments with your own text. Keep the surrounding
`<p class="bio">` and `</p>` tags. For example:

```html
<p class="bio">
  Write a few sentences about yourself, your work, and your interests here.
</p>
```

To add another paragraph, add another `<p class="bio">...</p>` inside the bio
comments. You can also customize the page's `<title>` and description in `<head>`.

## Update your photo

Replace `profile.jpeg` with your preferred portrait. A square image works best.
The photo appears beside your bio on larger screens and above it on smaller screens.

## Publications

The homepage links to [MaD-RL: Matching Distributions for Calibrating LLMs with
Reinforcement Learning](https://arxiv.org/abs/2609.31644) on arXiv, its PDF, and the
[Meta AI publication page](https://ai.meta.com/research/publications/mad-rl-matching-distributions-for-calibrating-llms-with-reinforcement-learning/).
The author list preserves the paper's author order and bolds **Jason Bohrer**.

To add a future publication, copy the `<article>` inside the publications section
in `index.html` and update its title, authors, year, and links. Give its heading a
unique `id` and use that same value for the article's `aria-labelledby`.

## Preview locally

Open `index.html` in your browser. Edits appear when you save and refresh.

You can also serve the site locally if Python 3 is installed:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Then visit <http://127.0.0.1:8000>. Press Ctrl+C in the terminal to stop the server.

## Publish on GitHub Pages

1. Commit and push these files to the `main` branch of `jnbrex/jnbrex.github.io`.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Select **main** and **/(root)**, then click **Save**.
5. Once deployment and the custom-domain setup below finish, visit <https://bohrer.ai/>.

Later changes publish when you commit and push to `main`. The `.nojekyll` file
tells GitHub Pages to serve the static files without a Jekyll build.
See [GitHub's publishing instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## Custom domain

The root `CNAME` file configures `bohrer.ai` as the custom domain for this
branch-published GitHub Pages site. Keep it when updating the website.

To finish the DNS setup in Cloudflare:

1. Open **bohrer.ai → DNS → Records → Import and Export**.
2. Import [dns/bohrer.ai.txt](dns/bohrer.ai.txt). It contains four apex `A`
   records, four apex `AAAA` records, and a `www` CNAME pointing to
   `jnbrex.github.io`. All nine records are configured as **DNS only**.
3. Open the repository's [Pages settings](https://github.com/jnbrex/jnbrex.github.io/settings/pages)
   and confirm **Custom domain** is `bohrer.ai` and the DNS check succeeds.
4. Enable **Enforce HTTPS** once GitHub's certificate is ready. GitHub notes
   that this option can take up to 24 hours to become available.

With DNS configured, GitHub Pages redirects `www.bohrer.ai` and the original
`jnbrex.github.io` address to the custom domain.

To verify domain ownership, open your account's [Pages settings](https://github.com/settings/pages),
add `bohrer.ai`, and add the TXT record GitHub provides in Cloudflare. Then
click **Verify** in GitHub and keep that TXT record.

References: [GitHub custom domains](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site),
[domain verification](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages),
and [Cloudflare DNS imports](https://developers.cloudflare.com/dns/manage-dns-records/how-to/import-and-export/).

## Files

- `index.html`: Your bio and publications.
- `styles.css`: Colors, typography, and responsive layout.
- `profile.jpeg`: Your profile photo.
- `.nojekyll`: Enables plain static-file publishing on GitHub Pages.
- `CNAME`: Sets the GitHub Pages custom domain to `bohrer.ai`.
- `dns/bohrer.ai.txt`: Cloudflare DNS import file for the custom domain.
- `README.md`: Editing, preview, and publishing instructions.
